# Finding Lane Lines on the Road
**Project solution by Luca Fiaschi 19/02/2017**

The goals is to make an image processing pipeline which detects lines on a video of a road.


## Method

My pipeline consisted of 5 steps. 

First, I converted the images to grayscale, then I use a canny edge detector to detect high grandient regions. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. I split the lines into right and left by looking at their inclination coeffiecients and then I take a robust median among all lines parameters.


## Shortcomings

The biggest shortcoming of this methods is that it contains several parameters which are not robust to lightning conditions.
Another problem is that one (or both) of the lines could not be visible. A final shortcoming is that we could have non straight lines but a sudden curve of the road.

## Improvements
There are several improvements that could be done to thos pipeline.
First of all, we need to achieve robustness to lightning conditions by smoothing furhter the images and detecting the region where the lines are probable to be and using more features than the canny edge detector (for example a classifier actually fusing multiscale canny detectors). Also when averaging across multiple lines there is only a certain number of possible orientations that we want to take into into account, as, for example, lines which are horizontal are not allowed.
Finally the frame by frame wigglines of the lines could be resolved by using a temporal smoothing method.