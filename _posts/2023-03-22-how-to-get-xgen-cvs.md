---
layout: post
title: "Maya XGen API"
author: "wano"
excerpt_separator: <!--more-->
tags: ['maya', 'xgen', 'dev']
use_math: true
lastmode: 2023-03-22 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

How to get control vertex positions in Maya XGen Interactive<!--more-->

```C++
#include <XGen/XgSplineAPI.h>

XGenSplineAPI::XgFnSpline splines;
{
    MDagPath dagPath = NodeNameToDagPath(fromNodeName);
    MFnDagNode nodeFn(dagPath);

    MPlug outRenderDataPlg = nodeFn.findPlug("outRender Data");
    MObject outRenderDataObj = outRenderDataPlg.asMObject();
    MPxData* outRenderDataPtr = MFnPluginDaga(outRenderDataObj).data();

    stringstream bs;
    outRenderDataPtr->writeBinary(bs);
    string bd = bs.str();

    const unsigned int tail = bd.size() % sizeof(unsigned int);
    const unsigned int padding = (tail>0) ? sizeof(unsigned int) - tail : 0;
    const unsigned int nElements = bd.size() / sizeof(unsigned int) + (tail>0 ? 1 : 0);

   splines.load(bs, nElements, 0);
}

MPointArray cvs:
{
    XGenSplineAPI::xgItSpline itr = splines.iterator();
    for(; !itr.isDone(); itr.next())
    {
        const unsigned int nCurves = itr.primitiveCount();

        const unsigned int stride = itr.primitiveInfoStride();
        const unsigned int* primitiveInfos = itr.primitiveInfos();

        const SgVec3f* positions = itr.positions(0);

        for(unsigned int i=0; i<nCurves; ++i)
        {
            const unsigned int& offset = primitiveInfos[i * stride];
            const unsigned int& length = primitiveInfos[i * stride + 1];

            const unsigned int& nCVs = length;

            for(unsigned int j=0; j<nCVs; ++j)
            {
                const unsigned int index = offset + j;

                const float& x = positions[index][0];
                const float& y = positions[index][1];
                const float& z = positions[index][2];

                cvs.append(MPoint(x, y, z));
            }
        }
    }
}
```