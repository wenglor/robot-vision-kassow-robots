# Set up Workcell
For the program execution, three persistent and global variables are required. Add them manually to the workspace.

|Variable name| Function|
|-------------|---------|
| g_calib_poses | An array of calibration poses. During the calibration procedure, the program iterates through the poses. Add, remove or update poses accordingly. A minimum number of five poses is highly recommended. |
| g_detection_pose | The pose that triggers the detection. Also used as a retreat pose for calibration step 2 if the camera is not mounted on the robot. The robot will move there, so you can remove the calibration plate to place it on the object ground. |
| g_use_case | A boolean flag to indicate where the camera is mounted:	<ul><li>0: Camera is mounted on the robot;</li><li>1: Camera is not mounted on the robot</li></ul> 	 | //TODO fix table formatting with HTML

Add the variables in the Workcell as persistent variables.

<img src="images/13%20workcell%20-%20persistent%20variables%20overview.png" alt="persistent_variables" class="medium"/>

Add, remove or update the pose variables.

<img src="images/14%20workcell%20-%20persistent%20variables%20g_calib_poses.png" alt="g_calib_poses" class="big"/>

Set the detection pose.

<img src="images/15%20workcell%20-%20persistent%20variables%20g_detection_pose.png" alt="g_detection_pose" class="big"/>

Select the use case.

<img src="images/16%20workcell%20-%20persistent%20variables%20g_use_case.png" alt="g_use_case" class="big"/>