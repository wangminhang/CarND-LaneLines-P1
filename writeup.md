# **Finding Lane Lines on the Road** 

## Writeup 

---

**Finding Lane Lines on the Road**

### 1. Reflection

The goals / steps of this project are the following:
* The pipeline that finds lane lines on the road is below:
Step 1: grayscale the image;
Step 2: Gaussian smoothing filter;
Step 3: Canny Edge Detection;
Step 4: select interest region;
Step 5: Hough Tranform line detection.

After get gray image from the native image,  apply Gaussian blur and the Canny edge detection algorithm for the gray image. I get the output image below:
[image1]: ./test_images_output/step3.jpg "Grayscale"
Then I define a four sided polygon to mask the image after appling the canny edge detection algorithm. And I get the output image below:
[image2]: ./test_images_output/step4.jpg "Grayscale"
Then I use the Hough transform and the modified the draw_line function with it and get the detected lines. 
[image3]: ./test_images_output/step5.jpg

---

In order to draw a single line on the left and right lanes, I modified the draw_lines() function as below:
step 1: seprarate left and right endpoints by the slope;
step 2: fitting a line and get the line‘s endpoints with polyfit and poly1d functions;
step 3: draw line with cv2:line function.



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that it can't handle the lane line of bend. I assume that the lane line in mask region will be straight, So it will be incorrect in bend.

Another shortcoming could be that the draw line function is not perfect. There are a lot of assumptions in function.
The pipeline is not robust enough.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to modified the pipeline with self-adaptive parametors, so as to improve the robustness.

Another potential improvement could be to add a histogram equalization step, so as to modify the image's quality.
