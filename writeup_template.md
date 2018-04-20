# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I use gaussian blur to reduce noise. After that I use Canny edge detection along with a region mask to determine lane marking edges. After doing canny edge detection, we can generate lines using a Hough transform. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking the max and min values of the list of x and y values for the left and right lanes. In the case where the max or min Y values dont extend to the middle of the view or the bottom of the view, I had to make a helper function for extend a line segment. 


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the threshold for the region mask isn't low enough in the middle of the view and edges are detected outside the lane region and skew the `draw_lines` function.

Another shortcoming is the use of min x values. By using the min x value the line will always extend to the outer edge of the lane marking instead of the ideal case where the x value is in the middle of the lane marking.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to determine the inner and outer lines for the lane markings in order to average their x values and place the bottom most point of a line overlay in the middle of the lane marking.
