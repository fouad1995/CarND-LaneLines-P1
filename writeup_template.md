# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline.

My pipeline consisted of 7 steps.<br>
1- Converting the images to grayscale<br>
2- Bluring the image using gaussian blur to remove the noise<br>
3- Apply Canny with higher values of low and high thresholds to ignore weak edges<br>
4- Apply get_roi_vertcies function which tries to estimate the best vertecies for ROI depend on the image shape<br>
5- Apply hough lines on the ROI image to detect lane lines<br>
6- Dilate image to try to connect lines ( some enhancement) <br>
7- Drawing the lane lines on image using weighted_img function<br>


I added some functions to helper functions to help me detect lanes correctly <br>
1- line_seperation : This function seprates 'lines' ie : seperate left and right lane lines The key concept is that the slope of the left lane line decreasing and the slope of the right lane line increasing<br>

2- get_points : This function returns the two points (x1,y1) , (x2,y2) to draw the fitted line using parameters (m,b)<br>

3- get_roi_vertecies : This funtion tries to estimate the best vertecies for ROI depend on the image shape <br>

### Note : I didn't modify the draw_lines() function but instead I passed input parameters to it correctly with each modification<br> 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the line will be curved the algorithm will fail 

Another shortcoming could be when the line deviate from the focus of the camera on the car ie ( lines become at very left or very right but the focus of the camera centered to image) so no lines will be detected.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to try to take the previous history of lines to prevent flikering 

Another potential improvement could be to try not depend on fixed ROI
