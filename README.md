# OpenCV Camera Calibration and Distortion Correction

This project performs **camera calibration** and **lens distortion correction** using **OpenCV** and a **chessboard pattern**.

## Project Goal
The purpose of this project is to:
- calibrate a camera using chessboard images extracted from a video
- estimate the camera intrinsic parameters
- estimate lens distortion coefficients
- correct geometric distortion in a video

---

## 1. Camera Calibration

### Calibration Method
A chessboard pattern was used for camera calibration.  
Frames were selected from a recorded chessboard video, and the inner corners were detected using OpenCV.

### Calibration Setup
- **Chessboard pattern:** 10 × 7 inner corners
- **Board cell size:** 0.025 m
- **Input type:** video frames
- **Selected images:** 19

---

## 2. Calibration Results

### Number of Selected Images
- **19**

### RMS Error
- **0.5108998650453123**

### Camera Matrix (K)
```python
[[973.76678888,   0.        , 642.19383273],
 [  0.        , 974.24352556, 356.24437884],
 [  0.        ,   0.        ,   1.        ]]
```

### Distortion Coefficients
```python
[ 0.04214937, -0.08523911, -0.00334514, 0.00214526, -0.47331148]
```

---

## 3. Interpretation of Results

The camera calibration was successfully completed using 19 selected images.

- The **RMS reprojection error** is **0.5109**, which indicates that the calibration result is reasonably accurate.
- The **camera matrix** represents the intrinsic camera parameters:
  - focal length in x and y directions
  - principal point (optical center)
- The **distortion coefficients** describe the lens distortion present in the camera.

These calibration values were then used for **distortion correction**.

---

## 4. Distortion Correction

Using the estimated camera matrix and distortion coefficients, geometric distortion in the input video was corrected.

### Correction Method
The distortion correction was performed using:
- `cv.initUndistortRectifyMap()`
- `cv.remap()`

This process generates a rectified output video with reduced lens distortion.

---

## 5. Files

### Main Files
- `camera_calibration.py` → performs camera calibration
- `distortion_correction.py` → corrects lens distortion
- `output.mp4` → input video (Videos excluded due to file size limits.)
- `corrected_output.mp4` → rectified output video (Videos excluded due to file size limits.)

---

## 6. Output

### Calibration Output
- Camera intrinsic matrix
- Distortion coefficients
- RMS calibration error

### Distortion Correction Output
- corrected video output
- visual comparison between original and rectified frames

![image](images/result.png)

---

## 7. Technologies Used
- Python
- OpenCV
- NumPy

---

## 8. Conclusion

This project demonstrates the basic process of:
1. camera calibration
2. lens distortion estimation
3. distortion correction

It shows how OpenCV can be used to estimate camera parameters and improve image geometry for computer vision tasks.
