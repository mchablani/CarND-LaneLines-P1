
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. These steps are very standard based on the concepts and pipeline covered in the lessons.
1. Convert image to gray grayscale
2. gaussian_blur
3. canny edge detection
4. Apply region of interest mask
5. Apply Hough transform to get lines
6. Line aggregation and extention to left and right lane detection
7. plot lines as overlay on original image.


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
1. Identifying lines with positive and negative slopes for left and right lanes.
2. Pick largest length line on left and right lane as representative.
3. Filter out lines with slopes not similar to representative
4. Using all the lines with slopes similar to representative pick min and max points and consider imaginary line between min and max points.
5. Extend the lines to the region using the slope of representative line and plot final extended line.

If you'd like to include images to show how the pipeline works, here is how to include an image:

![Generated images]
[image1]: ./modified_test_images/solidYellowCurve2.jpg "Sample"


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when Largest line detected with positive or negative slope is not part of the lane.

Another shortcoming could be region of interest is static and not dynamic.

Another shortcoming could be lanes are curve lanes rather than a line.

###3. Suggest possible improvements to your pipeline

A possible improvement would be to use length weighted average for positive and negative slope lines as representative.

Another potential improvement could be to handle curve lanes rather than assume its a line.
