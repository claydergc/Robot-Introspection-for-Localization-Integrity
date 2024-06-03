202405151816

Status: #idea

Tags: [[Bundle Adjustment]] [[slam]]

# Original Text

Bundle adjustment is a fundamental problem in computer vision and photogrammetry that involves refining the parameters of a 3D reconstruction model and the pose (position and orientation) of the cameras used to capture the images.

In the context of computer vision, bundle adjustment typically refers to the process of simultaneously refining the parameters of a 3D scene (such as the 3D coordinates of points in the scene) and the parameters of the cameras used to capture images of the scene. The goal is to minimize the reprojection error, which is the difference between the observed 2D image points and the projected 3D points in the image plane.

Bundle adjustment is important in tasks such as structure from motion (reconstructing 3D scenes from 2D images), simultaneous localization and mapping (SLAM), and 3D reconstruction from multiple images. It is a challenging optimization problem because it involves a large number of parameters and nonlinearities, and it is typically solved using iterative optimization techniques such as Levenberg-Marquardt or Gauss-Newton.

# In my own words

# References