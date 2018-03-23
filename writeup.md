
# **Finding Lane Lines on the Road** 

## Writeup

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

My pipeline consisted of 7 steps:
    - Converting the images to grayscale 
    - Smoothing the images
    - Detecting edges using Canny transform
    - Appling the mask to the detected edges, isolating only the region containing lanes 
    - Detecting line segments from edges with HoughLinesP function
    - Extrapolating lanes from line segments
    - Drawing lines on the original image
    

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. I divided line segments for left and right lane calculating their slopes. Line segment of the right lane should have positive slope and of the left lane negative. I calculated the center point of each line segment. Then by averaging I calculated center point and slope for each line. By using the equation of the line (y-y')=M(x-x') I computed the endpoints of both lines. I assumed that the y coordinate of lower point is the image height and the y coordinate of upper point is image height multiplied by 0.6 


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there will be poor lighting conditions

Another shortcoming could be when another car will be in the region of interest

Another shortcoming could be when the slope of right lane's segment is not positive, or slope of left lane's segment is not negetive. This happens on turns. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use other color spaces like HSL and HSV

Another potential improvement could be to crop all obstucting objects before detecting lanes

Another potential improvement could be to filter line segments by the position of its center. the x coordinate of right segments center should be bigger that half of the image width.

