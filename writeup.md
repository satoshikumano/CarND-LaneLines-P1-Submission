# **Finding Lane Lines on the Road** 

### Reflection

### 1. About my pipeline

My pipeline consisted of following steps.

- Apply gray scale to the image.
- Apply gaussian blur.
- Apply canny edge detection.
- Mask images outside the specified polygon.
- Line detection by HoghLinesP.
- Identify single line on the left and right lanes.
- Draw lines on the original image.

In order to draw a single line on the left and right lanes,
I modified the draw\_lines() function as following.

- Calculate the slope of each lines detected by HoghLinesP.
- If the slope is negative, the line may consist a left lane and vice versa.
- Ignore the line whose absolute value of slope is less than 0.4 since
they are too gentle to be regarded as lanes.
- Calculate the average of the slope and intercept for the left and right lanes
respectively.
- Calculate the x coordinate of top/ bottom of the line where y is 320 and 540
with the calculated average slope and intercept.

### 2. Potential shortcomings with my pipeline

1. Assumes fixed resolution of the image when calculate polygon mask and drawing
extrapolated line.
Need adjusting the program when the camera spec is changed.

1. Won't works in Sharp-breaking curve.

1. It depends on a lot adjusting parameters of HoughLineP. However it would 
be diffucult to optimize parameters to the various kind of images taken by the
equipped camera in reality.

### 3. Suggest possible improvements to your pipeline

1. Calculate the polygon mask and top/bottom y coordinates of the extrapolated
lines with the shape of the given image.

1. Use machine learning to classify the lane lines and otehr kind of lines.

