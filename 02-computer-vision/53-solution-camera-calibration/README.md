# Solution: Camera Calibration

> Part of: **Sensor and Camera Calibration**

## Additional Content

## Solution: Camera Calibration

Here is one example answer:
```
def cal_undistort(img, objpoints, imgpoints):
    ret, mtx, dist, rvecs, tvecs = cv2.calibrateCamera(objpoints, imgpoints, img.shape[1::-1], None, None)
    undist = cv2.undistort(img, mtx, dist, None, mtx)
    return undist
```
Note that the quiz is loading this image as channels first, so we use `img.shape[1::-1]` to get the height and width. This should be adjusted as necessary, such as is seen on the previous page for a grayscale image.
### Challenge: Calibrate your own camera!

If you're up for a challenge, go ahead and try these steps on your own camera images.  Just print out a [chessboard pattern](http://docs.opencv.org/2.4/_downloads/pattern.png), stick it to a flat surface, and take 20 or 30 pictures of it.  Make sure to take pictures of the pattern over the entire field of view of your camera, particularly near the edges.  

To extract object points and image points you can check out the Jupyter notebook in [this repository](https://github.com/udacity/CarND-Camera-Calibration).  If you're following along with the code in the notebook, be sure you set the right size for your chessboard, the link above is to a 9 x 6 pattern, while before we were using an 8 x 6.
