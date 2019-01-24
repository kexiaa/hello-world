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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussian smoothing, then I applied Canny edge detection, then I creaded a masked edges image. At last, I used the hough transfrom to find lanes from Canny edges.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. I first seperate the lines into two groups. One with positive slope and the other one with negative slope. Then I find the average slope of lines in two groups. Then I find the center of the lines in two groups. Based on the center and slope, I extropolate the lines. Therefore, I can get two lines.

Here is the result:

[image1]: ./result_img.png


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when if the road is not exactly in the middle of figure. Then it is not in the masked_edges and the problem may have some problem.

Another potential shortcoming would be that the draw_lines() did not work perfectly.


### 3. Suggest possible improvements to your pipeline
I think I may improve my draw_lines() function. In my code, I only used the sign of slope to seperate the lines. It is not accurate. I think I may include some other criterions to seperate the slope.
(1) The a < slope < b instead of slope > 0. We know the slope cannot be extreme small or extreme large. If I only use slope> 0, it may include some lines we do not want.
(2) Location of slope. We know the left slope is in the left side of figure. So maybe I can also add a constraint for this to make the selection of lines more accurate.
