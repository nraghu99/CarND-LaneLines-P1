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

My pipeline consisted of the following steps

1. got the image sizes and then made a copy of the input image
2. I then converted the copied image to grey scale and applied gaussian averager
3. Then i detected the edges using canny edges algorithm with a low threshold of 25 and high of 150
4. Then I marked a region of interest which is relative to the size of the image (no hard coding)
5. Ran hough transform to detect lines (lanes are lines!) from detected edges. These could be more than 1
line and also extraneous lines

I modified draw_lines() to only paint lines whose slopes were within an acceptable range i.e. no
horizontal lines (freeway driving)
so if the slope was between 0.5 and -0.5 i discarded those lines



If you'd like to include images to show how the pipeline works, here is how to include an image: 

![Solid White Right][image1]:./test_images_output/SolidWhiteRight.jpg


### 2. Identify potential shortcomings with your current pipeline


The biggest shortcoming is that my draw_lines is not very comprehensive. It does NOT average out the slopes
of the lines and then just draws 2  lines from the average slope and positions

The result is that you could have spurious line segments some times

### 3. Suggest possible improvements to your pipeline

Better draw lines function
