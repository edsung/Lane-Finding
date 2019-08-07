# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

![solidWhiteLines](https://github.com/edsung/Lane-Finding/blob/master/example_images/solidWhiteCurve.jpg)
![solidYellowLines](https://github.com/edsung/Lane-Finding/blob/master/example_images/solidYellowCurve.jpg)

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
First, I converted the images to grayscale, then the second step I applied a Gaussian Blur to grayscale image. 

Third, I used Canny Edge detection function to find the edges in the Gaussian Blur results. 

Fourth step is to mask the region of interest and pass through the Hough Transform. 

The fifth and final step is to draw the weighted lines onto the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by splitting the image into two halves. The Hough Transform lines coordinates for left lanes will be less than the x-coordinate of midpoint of the image and the line for right lanes are greater than the midpoint of the image, during the sorting process the lines are put into two lists.

I then separated out the x-coordinates and y-coordinates out of each list. I sorted each list in order to find minimum and maximum (x,y) coordinates, which corresponds with the longest line formed. The longest line is then extended to form the outline of a traffic line.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the image of road is of a major curve toward either left or right.

Another shortcoming could be if the lines are really faded out, leaving on horizontal lines on the road.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to able to update the mask as the image/scene is changing.

Another potential improvement could be to extrapolate the horizontal lines and calculate slope to draw the appropriate lines.
