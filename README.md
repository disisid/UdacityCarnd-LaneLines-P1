# UdacityCarnd-LaneLines-P1
Self Driving Nanodegree Project 1

Explanation of the Lane Detection Pipeline

First the given image is processed by converting to grayscale and then gaussian blur applied to this grayscale image. 
After this canny edge detection is applied to figure out the sharp and significant edges. 

After this the canny detected edge image is cropped for the region of interest i.e. only considering the central quadrilateral area that covers the lane lines. It is important to crop the region at this time as later other noise lines may interfere with hough lines extrapolation. 

After this we send the masked image thorough hough transform. The line segements identified by the hough transform are now to be identified into two key lanes - the right lane and left lane. The right lane must have -ve slope and the left lane positive however since the y-axis is reveresed in the image space, the right lane must have all lane segments with +ve slope and left lane with -ve slopes. 

The different line segments are sorted into two different lanes - the right lane and left lane after identifying their slopes. Once this is done, the lanes are averaged to get avergae slope and intercepts

After this the lines are simply drawn on a blank image and then added over the original image using weighted image function provided by opencv. 
