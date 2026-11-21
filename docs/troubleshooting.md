# Troubleshooting & FAQ

Common tracking failures, optimization divergence, and calibration issues in OpenVSLAM.

### Problem: Tracking state frequently enters 'LOST' mode
**Cause:** Insufficient ORB features detected due to low-contrast environments, rapid motion blur, or incorrect exposure settings.
**Resolution:** Increase `Feature.max_num_keypoints` to 2000 in your configuration file, or enable CLAHE histogram equalization in the image pre-processing pipeline.

### Problem: Global Bundle Adjustment fails to converge
**Cause:** Outlier landmark observations contaminating the pose graph after false loop detections.
**Resolution:** Tighten the loop detection chi-squared gating threshold in `module/loop_detector.cc` to reject erroneous match associations.
