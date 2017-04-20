# ROS_camera_calibration_steps

Step 1 :  
roslaunch usb_cam usb_cam-test.launch  
rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.024 image:=/usb_cam/image_raw camera:=/camera --no-service-check  

note : the total detected number of squares is 8x6, and the squares length is 0.024 m  

Step 2 :  
After calibration, you will see ost.yaml in /tmp  
To fix the below problem  
[ WARN] [1487843002.396523076]: Camera calibration file /home/odroid/.ros/camera_info/head_camera.yaml not found  
We have to do the following tasks  
cd ~/.ros  
mkdir camera_info  
Rename your ost.yaml to head_camera.yaml, then put into /home/odroid/.ros/camera_info  
Rename the camera_name in head_camera.yaml from narrow_stereo to head_camera, then  
you finish the camera calibration  
