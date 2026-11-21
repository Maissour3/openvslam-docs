# Supported Camera Models & Calibration Protocols

Accurate camera calibration is essential for stable visual SLAM pose estimation. OpenVSLAM supports multiple optical projections through specialized calibration parameters.

## Camera Model Comparison

| Camera Projection | Parameter Count | Lens Distortion Model | Typical FOV | Primary Application |
| :--- | :--- | :--- | :--- | :--- |
| **Perspective (Pinhole)** | 4 (fx, fy, cx, cy) | Brown-Conrady (k1, k2, p1, p2) | 60° - 90° | Industrial Inspection, Webcams |
| **Fisheye (Kannala-Brandt)** | 4 (fx, fy, cx, cy) | Equidistant polynomial (k1..k4) | 120° - 190° | Autonomous Vehicles, Drones |
| **Equirectangular** | 2 (width, height) | 360° Spherical Projection | 360° x 180° | VR Cameras, Panoramic SLAM |
| **Stereo Baseline** | 5 (fx, fy, cx, cy, b) | Epipolar Rectification | 75° | Depth Sensing, Mobile Robotics |

## Calibration Workflow
Calibration involves capturing at least 30 checkerboard or AprilTag images from diverse angles and calculating intrinsic matrices using OpenCV calibration routines before populating OpenVSLAM YAML configuration files.
