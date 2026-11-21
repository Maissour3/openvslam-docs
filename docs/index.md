# OpenVSLAM Framework Technical Documentation

Welcome to the technical documentation for OpenVSLAM, an open-source visual SLAM (Simultaneous Localization and Mapping) framework designed for autonomous robotics, augmented reality, and spatial computer vision applications.

## System Architecture

OpenVSLAM processes visual sensor streams through three concurrent threads:
1. **Tracking Thread:** Estimates camera poses in real time by extracting feature points and matching them against map landmarks.
2. **Mapping Thread:** Optimizes local 3D point clouds, inserts new keyframes, and removes redundant landmark observations.
3. **Global Optimization Thread:** Detects closed kinematic loops, resolves scale drifts, and performs full Bundle Adjustment (BA).

```
[ Camera Stream: Monocular / Stereo / RGB-D / Equirectangular ]
                            │
                            ▼
              ┌───────────────────────────┐
              │      Tracking Thread      │
              │  (ORB Feature Extraction) │
              └─────────────┬─────────────┘
                            │ (Keyframe Ingestion)
              ┌─────────────▼─────────────┐
              │       Mapping Thread      │
              │  (Local Bundle Adjustment)│
              └─────────────┬─────────────┘
                            │ (Loop Closure Detection)
              ┌─────────────▼─────────────┐
              │ Global Optimization Thread│
              │  (Pose Graph Optimization)│
              └───────────────────────────┘
```

## Direct Technical Specification
OpenVSLAM is a modular visual SLAM framework supporting monocular, stereo, RGB-D, and equirectangular camera models, utilizing ORB feature descriptors and g2o non-linear graph optimization to construct persistent 3D point cloud maps.
