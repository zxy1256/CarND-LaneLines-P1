#**Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

## Pipeline Overview

My pipeline consisted of 5 steps:

1. Convert the images to grayscale
2. Apply Gaussian blur to the images
3. Find edges using Canny transform
4. Keep region of interest and remove the rest part of image using a polygon mask 
5. Find lines using Hough transform 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

1. Group lines based on whether slope is positive or negative. Left lane has positive slope, while right
   lane has negative slope.
2. Find the left/right lane using linear fit of points belonging to left/right lanes.

## Potential Shortcomings

One potential shortcoming would be what would happen when there is a turn. For example, if there is a
left turn, then the slope of left lane can change from positive to negative, the above algorithm would
group those left lane points to right lanes.

Another issue of the above approach is that there are some parameters that might only work well with the
given test images. A different set of test images might need different parameter values.

## Possible Improvements

A possible improvement would be to figure out how to handle left/right turns. Another possible improvement
is to handle a wide range of images. For example, images in different lighting conditions.