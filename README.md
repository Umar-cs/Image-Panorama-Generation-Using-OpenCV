# Image Panorama Generation Using OpenCV

## Overview

This project demonstrates how to create a seamless panoramic image by automatically combining multiple overlapping photographs. The implementation utilizes OpenCV's built-in image stitching pipeline, which detects common visual features, aligns images geometrically, and blends them into a single high-quality panorama. Additional post-processing techniques are applied to remove unwanted borders and improve the final output.

## Project Workflow

The panorama generation process consists of the following stages:

1. **Feature Detection**

   * Detect distinctive interest points from each input image using robust feature detection techniques.
   * Extract feature descriptors that remain reliable under changes in scale, rotation, and illumination.

2. **Feature Matching**

   * Compare descriptors across images to identify corresponding points between overlapping regions.
   * Retain only the strongest and most reliable matches.

3. **Homography Estimation**

   * Estimate the geometric transformation that relates one image to another.
   * Apply the RANSAC algorithm to eliminate incorrect feature matches and compute an accurate homography matrix.

4. **Image Warping and Alignment**

   * Warp the input images according to the estimated transformation.
   * Align all images into a common coordinate system.

5. **Image Blending**

   * Merge overlapping regions smoothly to minimize visible seams and exposure differences.
   * Generate a continuous panoramic image.

6. **Post-Processing**

   * Add temporary borders where necessary for processing.
   * Detect the valid panorama boundaries.
   * Crop unnecessary black regions to produce a clean final result.

## OpenCV Functions Used

### `cv2.Stitcher_create()`

Creates an OpenCV panorama stitching object that automates feature detection, feature matching, camera parameter estimation, image alignment, exposure compensation, and blending.

**Modes**

* `PANORAMA` – Optimized for panoramic photography.
* `SCANS` – Intended for scanned documents and flat images.

### `cv2.Stitcher.stitch()`

Combines multiple overlapping images into a single panoramic output.

### `cv2.copyMakeBorder()`

Adds padding around an image, which is useful during border handling and cropping operations.

### `cv2.findContours()`

Extracts object boundaries from binary images, allowing detection of the valid panorama region for automatic cropping.

## Features

* Automatic panorama creation
* Robust feature matching
* Outlier rejection using RANSAC
* Perspective correction through homography estimation
* Smooth image blending
* Automatic removal of black borders
* High-quality panoramic output using OpenCV

## Requirements

* Python 3.x
* OpenCV (`opencv-python`)
* NumPy

## Output

The program accepts a set of overlapping images and produces a single stitched panoramic image with minimal distortion and clean boundaries.
