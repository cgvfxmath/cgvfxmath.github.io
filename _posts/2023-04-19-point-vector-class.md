---
layout: post
title: "C++ 3D Point & Vector Class"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'C++', 'opencv', 'eigen3']
use_math: true
lastmode: 2023-03-23 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Making C++ 3D Point & Vector Class compatible with Eigen and OpenCV<!--more-->

```cpp
#include <iostream>
using namespace std;

#include <Eigen/Core>
#include <opencv2/core.hpp>

template <typename T>
class Tuple3
{
    public:

        // three values
        union
        {
            struct
            {
                union { T x; T u; };
                union { T y; T v; };
                union { T z; T w; };
            };
            T data[3];
        };

    public:

        // default constructor
        Tuple3()
        { x = y = z = T(0); }

        // class constructor (from three values)
        Tuple3(T X, T Y, T Z)
        { x=X; y=Y; z=Z; }

        // assignement operator (from Tuple3)
        Tuple3& operator=(const Tuple3& t)
        { x=t.x; y=t.y; z=t.z; return (*this); }

        // access operator
        T& operator[](const int& index)
        { return data[index]; }

        // access operator (const ver.)
        const T& operator[](const int& index) const
        { return data[index]; }

        ////////////////////
        // from/to Eigen3 //
        #ifdef EIGEN_MAJOR_VERSION
        template <typename S, int N>
        Tuple3(const Eigen::Vector<S,N>& v)
        { for(int i=0;i<3;++i) { data[i] = T(v[i]); } }

        template <typename S, int N>
        Tuple3& operator=(const Eigen::Vector<S,N>& v)
        { for(int i=0;i<3;++i) { data[i] = T(v[i]); } return (*this); }

        template <typename S, int N>
        operator Eigen::Vector<S,N>() const
        { Eigen::Vector<S,N> tmp; for(int i=0;i<3;++i) { tmp[i] = S(data[i]); } return tmp; }
        #endif

        ////////////////////
        // from/to OpenCV //
        #ifdef CV_VERSION_MAJOR
        template <typename S>
        Tuple3(const cv::Point_<S>& p)
        { x=T(p.x); y=T(p.y); z=1.0; }

        template <typename S>
        Tuple3& operator=(const cv::Point_<S>& p)
        { x=T(p.x); y=T(p.y); z=1.0; return (*this); }

        template <typename S>
        operator cv::Point_<S>() const
        { return cv::Point_<S>(S(x/z), S(y/z)); }
        #endif
};

template <typename T>
ostream& operator<<(ostream& os, const Tuple3<T>& t)
{
    os << "( " << t.x << ", " << t.y << ", " << t.z << " )";

    return os;
}

typedef Tuple3<double> MyPoint;
typedef Tuple3<double> MyVector;

int main(int argc, char* argv[])
{
    // vector
    {
        MyVector v(1, 2, 3);
        cout << v << endl; // ( 1, 2, 3 )

        Eigen::Vector3d v_eg = v;
        cout << v_eg << endl; // 1 2 3

        MyVector vv = v_eg;
        cout << vv << endl; // ( 1, 2, 3 )
    }

    // point
    {
        MyPoint p(1, 2, 3);
        cout << p << endl; // ( 1, 2, 3 )

        cv::Point2d p_cv = p;
        cout << p_cv << endl; // [0.333333, 0.666667]

        MyPoint pp = p_cv;
        cout << pp << endl; // ( 0.333333, 0.666667, 1 )
    }

    return EXIT_SUCCESS;
}
```
