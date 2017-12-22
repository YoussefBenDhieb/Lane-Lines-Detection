# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 7 steps. First, I selected the yellow and white colors only, then I converted the images to grayscale and applied a Gaussian Blur with a kernel equal to 3. After that, I applied the Canny transform to detect the edges using thresholds 10 and 255, then I selected the region of interest only. Finally, I applied the hough transform to find the lines and draw them and combined the images.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding the slope of each line and its intercept and divided them in two groups: lines with positive slopes and lines with negative slopes. Also, I eliminated the lines with  slopes between [-0.3 0.3] to avoid including lines near the horizontal axis. After that, I averaged the lines of each group taking into account their weights (lengths) to obtain only two lines (one average line for each group). Then, I extrapolated the line to reach the extents of the region of interest.



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lines are curved. 

Another shortcoming could be that we can obtain only one line if the car rotates while changing of lane in a manner that all the slopes will have the same sign.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to include the detection of the curved lines using more advanced computer vision algorithms like the B-spline or the Generalized Hough Transform.

Another potential improvement could be to convert the image from RGB to other colormaps like HSV or HSL to select the yellow and white lane lines.
