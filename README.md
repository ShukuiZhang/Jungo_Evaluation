# Jungo_Evaluation
## Summary:   
collect a bunch of gaze images with observer looking at different points through known head pose and gaze direction 

## You need to know:   
1. One session takes only one row out of the three rows				
2. In each session, your face should only head to RED points, however your gaze visit all points in a row  
3. One session is composed of 9 sets, with 7 normal sets and 2 edge sets. In each set, you should fix your head pose and only change gaze direction, ie. looking at a specific point belongs to this set								
4. In each set, you should fix your head pose to the direction such that when you look forward natually with such pose, your gaze is focused on the center red point (in that set) of the middle row				
5. Points in each set will visited from left to right				
6. If you think last image was not taken correctly, let the controller know and we should retake it				
7. Each image was taken by left-clicking the mouse				

### normal set:
contains 7 points, i.e. left red points, center red points, right red points and the 4 blue points in between.				
### edge set: 
contains 4 points, i.e. left (or right) red points, center red points and the 2 blue points in-between

## Calibration offline: 
1. measure the real distance/ relative positon between camera center and driver chin tip (the origin)
2. make the experiment setup of similar relative position
3. use checkerboard to capture 10 - 15 images, which is used to compute the extrinsics from the chin origin to camera center, this is to further refine the 3D transformation				

## Session starts:
At the beginning of each session, controller will first make sure your eyes are of the same height with the center row of lines and also your chin rest at our origin				
```
for each set:				
    find the center red point in middle row and fix your head pose by natually looking at that point with neutual gaze 				
    figure out the left red point and right red point for this set, note left/right red point may also be the center point if this set if an edge set
    for point_ in [left_red_point: right_red_point]: //this may contain 4 or 7 points
        focused on point_ and take the picture by left-clicking the mouse, you should hear the shutter ticking if successful
```        
