# **Finding Lane Lines on the Road** 

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied gaussian blur with kernel of size 5 to grey image. My next step was to apply canny algorithm with predefined low and high thresholds. Given edges detected by canny method I've selected region I'm interested in be defining verticies which defined trapezoid region on image.
Such selected region was then passed to Hough Line Transform to detect which points creates straight lines. These lines where then drawn by draw_lines function and resulting image was layered on true image for final result.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by segregating which points creates line with positive or negative slope. After this I've eliminated outliers (for both slope and intercept) based on how many standard deviation from mean given slope or intercept is.
Such filtered result was then averaged and used to compute two lines (one fro positive and one for negative slope) from top to bottom of selected trapezoid.


### 2. Identify potential shortcomings with your current pipeline

First potential shortcoming would be lighting which lower gradient for line and therefore points won't be detected by Canny method. 

Second shortcoming would be to detect false lines which are just deformations/imperfections on road.

Third shortcoming would be detecting curved line.


### 3. Suggest possible improvements to your pipeline

Better way of detecting and removing outlier lines (slope, intercept and positions).

Using polynomials to detect curved line.
