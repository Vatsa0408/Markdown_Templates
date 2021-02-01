# Low Definiton CRO Ground Truth Generation with GoPro camera (PoC)

## Table of contents
1. [Introduction](#introduction)

  1.1. Situation
  1.2. Problem
  1.3. Solution
2. [Method](#method)
  2.1. Toolchain
3. Validation
  3.1. Method
  3.2. Comparision with atlatec
4. [Improvement](#improvement)
4. Improvement

## 1. Introduction
This chapter will give a short overview about the need of that method.
##### 1.1 Situation
At the moment road measurement is getting more important for autonomous driving.
The number of camera sensors is also increasing in that field.
##### 1.2 Problem
The process of measuring road data is quite long. Measuring, processing and data storage takes time. In some
situation the process of measuring the roads take to long.
##### 1.3 Solution
With this method we can measure the roads faster.   


## 2. Method

##### 2.1 Toolchain

## 3. Validation

##### 3.1 Method

##### 3.2 Comparision with atlatec

## Improvement


## Design

1. Consider the B19_S right lane right side lane edge 'P0' for PoC

1. Calcualte the VO_D2L(P0) from FR Wheel to side lane

1. Relcoalize the Vehicle IMU POI5 (lat,Lon) using VO_D2L + Distance (POI5 to FR wheel). Here, POI5 is the centre point between the Front wheels

1. Save the process data in line_P0_LDVO_maps_b19_S.csv with lat, lon and INS_GPS_status

1. Compare the processed Line P0 data with developed Atlatec data (Line P0))

## comparision

> Accuracy

Average: -19 cm, +/- 20 cm

> Observations

* B_19_S track

![B_19 South track](./images_observation/B19_S.PNG)

Legends:

1. White = Ataltec_GT_P0
1. Green = LDVO_P0
1. Turquoise = Vehcile IMU position (POI5)

* When the track turns to left, LDVO points are in allign to Atlatec points
![B_19_obs_curve_left](./images_observation/curve_left.PNG)

* when the track turns to right, LDVO points are making differnece with Atlatec points (negative shift)
![B_19_obs_curve_right ](./images_observation/curve_right.PNG)

* Image processing D2L - Noise detection
![image_processing_noise_detection](./images_observation/image_processing_noise_detection.PNG)

* Camera Calibration method need to check properly for LDVO maps generation - needs very presice calibration data

* Vehicle INS_Yaw angle turning logic need to understand and check the logic

* Improve image processing D2L, Noise detection due to full sunny conditoins

## Improvement in Accuracy results & Observations

> Improve Accuarcy

Average: -1 cm, +/- 10 cm

Legends:

1. White = Ataltec_GT_P0
1. Yellow = LDVO_P0
1. Turquoise = Vehcile IMU position (POI5)

![image_processing_noise_detection](./images_observation/accuracy_improve.PNG)

> Observations

* As this LDVO processed data are original without any filteration. So, This Accuracy is understandable.

* Found some errors in Previous method regarding, Vehicle INS Yaw anngle roatation for Line_P0 (lat, lon) calculation.

> Improvement Steps

1. Improved the camera calibration caclulation and Image processing for D2L, also observe the every points on Qgis

1. Understand the Vehicle INS yaw angle rotation logic

1. Mostly noise had detected because of full sunny / Tunnels conditions during D2L processing.

1. For development of the LDVO maps need to measure the data wihtout full sun, like morning / evening, clouds or normal light conditoin.

> Comaprison analysis

![comparision](./images_observation/LD_Ground_Truth_GoPro_onBoard_atlatec_Maps.png)
