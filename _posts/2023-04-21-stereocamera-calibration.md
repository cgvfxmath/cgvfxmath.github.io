---
layout: post
title: "Stereocamera Calibration"
author: "wano"
excerpt_separator: <!--more-->
tags: ['opencv', 'dev']
use_math: true
lastmode: 2023-04-21 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

It is the process of aligning two cameras and correcting any distortions to achieve precise depth perception.<!--more-->

```python
import sys, glob
import numpy as np
import matplotlib.pyplot as plt
import cv2 as cv

# ChArUco photo images
IMAGES_PATH_LEFT = 'C:\data\cam_left\*.jpg'
IMAGES_PATH_RIGHT = 'C:\data\cam_right\*.jpg'

imgPathsLeft = sorted(glob.glob(IMAGES_PATH_LEFT))
imgPathsRight = sorted(glob.glob(IMAGES_PATH_RIGHT))

imgListLeft = []
imgListRight = []

for imgPathLeft, imgPathRight in zip(imgPathsLeft, imgPathsRight):
    imgL = cv.imread(imgPathLeft)
    imgR = cv.imread(imgPathRight)
    imgListLeft.append(imgL)
    imgListRight.append(imgR)

imgSizeL = imgListLeft[0].shape[:2][::-1]
imgSizeR = imgListRight[0].shape[:2][::-1]

imgWidthL, imgHeightL = imgSizeL[0], imgSizeL[1]
imgWidthR, imgHeightR = imgSizeR[0], imgSizeR[1]

# ChArUco pattern
cols, rows = 6, 9
patternSize = 1.0
markerSize = 0.5
arucoType = cv.aruco.DICT_4X4_100
dictionary = cv.aruco.getPredefinedDictionary(arucoType)
calibrationBoard = cv.aruco.CharucoBoard((cols, rows), patternSize, markerSize, dictionary)
parameters = cv.aruco.DetectorParameters()
detector = cv.aruco.ArucoDetector(dictionary, parameters)

# 3D corner points in world space (the answer)
worldCornerPoints = np.zeros(((cols-1)*(rows-1), 3), np.float32)
worldCornerPoints[:,:2] = np.mgrid[1:cols, 1:rows].T.reshape(-1,2) * patternSize
worldCornerPointsAccum = [] # from all images

# detected corner info. (point-ID pairs) from all images
cornerPointsAccumL = []
cornerPointsAccumR = []
cornerIdsAccumL = []
cornerIdsAccumR = []

# solver options
terminationCriteria = (cv.TERM_CRITERIA_MAX_ITER + cv.TERM_CRITERIA_EPS, 100, 0.00001)
flagsForSingleCamCalib = cv.CALIB_FIX_PRINCIPAL_POINT
flagsForStereoCamCalib = (cv.CALIB_FIX_INTRINSIC + cv.CALIB_FIX_PRINCIPAL_POINT)

for imgL, imgR in zip(imgListLeft, imgListRight):

    grayL = cv.cvtColor(imgL, cv.COLOR_BGR2GRAY)
    grayR = cv.cvtColor(imgR, cv.COLOR_BGR2GRAY)

    corners, ids, rejected = cv.aruco.detectMarkers(grayL, dictionary)
    corners, ids, rejected, recovered = cv.aruco.refineDetectedMarkers(grayL, calibrationBoard, corners, ids, rejected)

    if corners == None or len(corners) == 0:
        print('Error', file=sys.stderr)
        continue

    for corner in corners:
        cv.cornerSubPix(grayL, corner, winSize=(10,10), zeroZone=(-1,-1), criteria=terminationCriteria)

    numDetectedCornersL, cornerPointsL, cornerIdsL = cv.aruco.interpolateCornersCharuco(corners, ids, grayL, calibrationBoard)
    cornerPointsAccumL.append(cornerPointsL)
    cornerIdsAccumL.append(cornerIdsL)

    corners, ids, rejected = cv.aruco.detectMarkers(grayR, dictionary)
    corners, ids, rejected, recovered = cv.aruco.refineDetectedMarkers(grayR, calibrationBoard, corners, ids, rejected)

    if corners == None or len(corners) == 0:
        print('Error', file=sys.stderr)
        continue

    for corner in corners:
        cv.cornerSubPix(grayR, corner, winSize=(10,10), zeroZone=(-1,-1), criteria=terminationCriteria)

    numDetectedCornersR, cornerPointsR, cornerIdsR = cv.aruco.interpolateCornersCharuco(corners, ids, grayR, calibrationBoard)
    cornerPointsAccumR.append(cornerPointsR)
    cornerIdsAccumR.append(cornerIdsR)

    worldCornerPointsAccum.append(worldCornerPoints)

############# Camera Calibration ################################################
# k: intrinsic parameters (3x3 matrix)
# d: distortion coefficients (1x5 matrix)
# rVecs: rotation vector (Rodrigues representation that is how OpenCV functions represent rotation)
# tVecs: translation vector

# for the 1st camera (left)
rmseL, kL, dL, rVecsL, tVecsL = cv.aruco.calibrateCameraCharuco(
    charucoCorners = cornerPointsAccumL,
    charucoIds = cornerIdsAccumL,
    board = calibrationBoard,
    imageSize = imgSizeL,
    cameraMatrix = None, distCoeffs = None,
    flags = flagsForSingleCamCalib,
    criteria = terminationCriteria)

# for the 2nd camera (right)
rmseR, kR, dR, rVecsR, tVecsR = cv.aruco.calibrateCameraCharuco(
    charucoCorners = cornerPointsAccumR,
    charucoIds = cornerIdsAccumR,
    board = calibrationBoard,
    imageSize = imgSizeR,
    cameraMatrix = None, distCoeffs = None,
    flags = flagsForSingleCamCalib,
    criteria = terminationCriteria)

######### Stereo Vision Calibration #############################################

rmse, _, _, _, _, R, T, _, _ = cv.stereoCalibrate(
    objectPoints = worldCornerPointsAccum,
    imagePoints1 = cornerPointsAccumL,
    imagePoints2 = cornerPointsAccumR,
    cameraMatrix1 = kL, distCoeffs1 = dL,
    cameraMatrix2 = kR, distCoeffs2 = dR,
    imageSize = imgSizeL,
    R = None, T = None, E = None, F = None,
    flags = flagsForStereoCamCalib,
    criteria = terminationCriteria)
```

