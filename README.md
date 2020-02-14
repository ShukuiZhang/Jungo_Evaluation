# Jungo_Evaluation
## Summary:   
Collect gaze images with observer looking at different points. Images are captured by observer left-clicking the mouse when he/she feels good regarding the current gaze direction.

### normal set:
![normal set] (Selection_224.png)  
Format: ![Alt Text](url)
contains 7 points, i.e. left red points, center red points, right red points and the 4 blue points in between.				

### edge set: 
![edge set] (Selection_225.png)  
Format: ![Alt Text](url)
contains 4 points, i.e. left (or right) red points, center red points and the 2 blue points in-between

## You need to know:   
**One session**:
* composed of 9 sets, with 7 normal sets and 2 edge sets. E

**In a session**:  
* only visit points in one row
* your face only head to RED points, however your gaze visit all points in a row  

    **In a set**: 
    fix your head pose to center red point and only change gaze direction by looking at points in this set, once a time, from left to right    
    
**More details**:    
* In each set, you should fix your head pose to the direction such that when you look forward natually with such pose, your gaze is focused on that set center red point of **the middle row**				
* Points in each set will visited from left to right				
* If you think last image was not taken correctly, let the controller know and we should retake it				
* Each image was taken by left-clicking the mouse				
* Note left/right red point may also be the center point if this set if an edge set

## Calibration offline: 
1. measure the real distance/ relative positon between camera center and driver chin tip (the origin)
2. make the experiment setup of similar relative position
3. use checkerboard to capture 10 - 15 images, which is used to compute the extrinsics from the chin origin to camera center, this is to further refine the 3D transformation				

## Session starts:
At the beginning of each session, controller will first make sure your eyes are of the same height with the center row of lines and also your chin rest at our origin				
```
for each set:				
    find the center_red_point in middle row and fix your head pose by looking at that point natually 				
    find the range of points in this set, 
    for point_ in [left_red_point: right_red_point]: //this may contain 4 or 7 points, from left to right
        focused on point_ and take the picture by left-clicking the mouse, you should hear the shutter ticking if successful
        (repeat this process for next point)
```        
