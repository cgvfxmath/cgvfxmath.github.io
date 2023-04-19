---
layout: post
title: "C++ Image Class"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'C++', 'opencv', 'eigen3']
use_math: true
lastmode: 2023-04-19 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Making C++ Image class based on OpenCV<!--more-->

```cpp
#include <opencv2/core.hpp>
#include <opencv2/highgui.hpp>

class Image
{
private:

    cv::Mat mMat;

    std::string mPath;

    int mWidth = 0;
    int mHeight = 0;
    int mChannels = 0;

public:

    Image() {}

    void reset()
    {
        mMat.release();
        mPath.clear();
        mWidth = mHeight = mChannels = 0;
    }

    Image& operator=(const Image& img)
    {
        Image::reset();

        mMat = img.mMat.clone();

        mPath = img.mPath;
        mWidth = img.mWidth;
        mHeight = img.mHeight;
        mChannels = img.mChannels;

        return (*this);
    }

    // RGB-order) k: 0=Red, 1=Green, 2=Blue
    unsigned char& operator()(int i, int j, int k = 0)
    {
        return mMat.data[mChannels * (j * mWidth + i) + (2 - k)]; // 2-k: BGR -> RGB
    }

    const unsigned char& operator()(int i, int j, int k = 0) const
    {
        return mMat.data[mChannels * (j * mWidth + i) + (2 - k)]; // 2-k: BGR -> RGB
    }

    Image& create(int width, int height, int channels)
    {
        reset();

        mMat = cv::Mat::zeros(height, width, CV_MAKETYPE(CV_32F, channels)); // black image

        mWidth = width;
        mHeight = height;
        mChannels = channels;

        return (*this);
    }

    int width() const
    {
        return mWidth;
    }

    int height() const
    {
        return mHeight;
    }

    int channels() const
    {
        return mChannels;
    }

    cv::Size size() const
    {
        return cv::Size(mWidth, mHeight);
    }

    cv::Mat& mat()
    {
        return mMat;
    }

    const cv::Mat& mat() const
    {
        return mMat;
    }

    bool load(const std::string& path)
    {
        if (mPath == path) { return true; } // same file handling

        reset();

        mPath = path;

        mMat = cv::imread(path.c_str(), cv::IMREAD_UNCHANGED);

        mWidth = mMat.cols;
        mHeight = mMat.rows;
        mChannels = mMat.channels();

        return true;
    }

    bool empty() const
    {
        return mMat.empty();
    }

    void show(const char* title = "Image Test", int delay = -1 /*sec*/) const
    {
        if (empty()) { return; }
        cv::namedWindow(title, cv::WINDOW_NORMAL);
        cv::resizeWindow(title, mWidth, mHeight);
        cv::imshow(title, mMat);
        cv::waitKey(delay * 1000); // 1000: sec. to msec.
    }
};

int main(int argc, char* argv[])
{
    Image img;
    img.load("C:/test.jpg");
    img.show("Image Test", 3);

    return EXIT_SUCCESS;
}
```
