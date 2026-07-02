# Set up Workcell

For the program execution, two persistent and global variables are required. Add them manually to the workspace.

| Variable name | Function |
|---------------|----------|
| `g_detection_pose` | The pose that triggers the detection. Also used as a retreat pose for calibration step 2 if the camera is not mounted on the robot. The robot will move there, so you can remove the calibration plate to place it on the object ground. |
| `g_reference_frame` | The pose that is used as a reference frame for other poses. It is updated in the program to also update the related poses. |

Add the variables in the Workcell as persistent variables.

<img src="images/13%20workcell%20-%20persistent%20variables%20overview.png" alt="persistent_variables" class="medium"/>

Set the detection pose.

<img src="images/15%20workcell%20-%20persistent%20variables%20g_detection_pose.png" alt="g_detection_pose" class="big"/>

## Open Program and Setup Variables

Open the program from the USB stick to set up the program variables.

| Variable name | Function |
|---------------|----------|
| `WU_CALIB_POSES` | An array of the calibration poses. During the calibration procedure, the program iterates through the poses. You can add, remove or update poses here. A minimum number of five poses is required. |
| `WU_MACHINE_POSES_TAUGHT` | A numeric flag that is used to separate the `update_reference_frame` use case into the preparation and the runtime. Before teaching the poses related to the reference frame, the reference frame needs to be set. When this is done, you can set the value to `1`. |
| `WU_USE_CASE` | A numeric flag to indicate where the camera is mounted:<ul><li>`0`: Camera is mounted on the robot</li><li>`1`: Camera is not mounted on the robot</li></ul> |

Add, remove or update the pose variables, then select the use case.
