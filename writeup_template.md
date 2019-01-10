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

My pipeline consisted of 5 below steps.

  1. Conversion the images to grayscale.
  2. Define a kernel size and apply Gaussian smoothing on grayscale image. I got blur grey image object after it.
  3. Define our parameters(thresholds) for Canny and apply it to image
  4. Define the Hough transform parameters, get reason of interest masked image and apply Hough transformation with draw lines.
  5. Merge the original image with transformed image and get the final detected lined image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating slope and get average values of coordinate points. After change, this function gives flexibility in drawing lines due to many calculations for getting stable and accurate thick linings of the road lane lines.

Original Image:
![Original Image][test_images/solidWhiteCurve.jpg]

Transformed Image after Detect Lane Lines:
![Image after Lane Detected][test_images_output/solidWhiteCurve.jpg]


### 2. Identify potential shortcomings with your current pipeline

This program is elementory or too basic to understand the computer vision for driverless vehicles. This has a lot of shortcomings but in this scenario(elementory training), we lack of the following shortcomings.

One potential shortcoming would be what would happen when any white or off-white object come between of the road lanes. If this object comes under region or area of iterest vertices, this is measured as part of lane lines.

Another shortcoming could be happen when shadow and contrast are available in the image. In this case, the program can get confused between the lane lines and the contrast of the image and calculate coordinates incorrectly to draw lines.

In heavy traffic conditions, there must be another logic to guide the vehicle for movement as this method is not sufficient to take decisions to go in particular right direction.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to get median of the block of lane line's length and compare this length with all detected lane line's or any white object's length. If this lenght is lesesr than average length, we can ignore this unwanted object.

