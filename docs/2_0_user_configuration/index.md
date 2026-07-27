# User Configuration

The robot program requires configuration of workcell variables and program variables to match your specific setup. This section describes all parameters you need to adapt.

## Workcell Variables

For the program execution, two persistent and global variables are required in the workcell. Add them manually to the workspace.

| Variable name | Type | Function |
|---------------|------|----------|
| `g_detection_pose` | Pose | The pose that triggers the detection. Also used as a retreat pose for calibration step 2 if the camera is not mounted on the robot. The robot will move there, so you can remove the calibration plate to place it on the object ground. |
| `g_reference_frame` | Pose | The pose that is used as a reference frame for other poses. It is updated in the program to also update the related poses. |

Add the variables in the Workcell as persistent variables.

<img src="images/13%20workcell%20-%20persistent%20variables%20overview.png" alt="persistent_variables" class="medium"/>

Set the detection pose.

<img src="images/15%20workcell%20-%20persistent%20variables%20g_detection_pose.png" alt="g_detection_pose" class="big"/>

## Program Variables

Open the program from the USB stick to set up the program variables.

### Boolean parameters

| Parameter | Description |
| --- | --- |
| `WU_MACHINE_POSES_TAUGHT` | Used within the `update_reference_frame` use case to stop the program so the related poses for the reference frame can be taught after the initial reference frame was set. After teaching the poses, set this value to `1`. |

### Numerical parameters

| Parameter | Description |
| --- | --- |
| `WU_USE_CASE` | A numeric flag to indicate where the camera is mounted: <ul><li>`0`: Camera is mounted on the robot</li><li>`1`: Camera is not mounted on the robot</li></ul> |

### Pose parameters

| Parameter | Description |
| --- | --- |
| `WU_CALIB_POSES` | An array of the calibration poses. During the calibration procedure, the program iterates through the poses. You can add, remove or update poses here. A minimum number of five poses is required. |

### String parameters (uniVision job names)

The following uniVision job names are used by default. If using different job names, update them in the program at the specified locations:

| Parameter | Default value | Description | Update location |
| --- | --- | --- | --- |
| Calibration job | `calibration.u3p` | Name of the uniVision job for calibration | `run_calibration` subprogram |
| Detection job | `find_objects.u3p` | Name of the uniVision job for object detection | `single_detection` and `multi_detection` subprograms |
| Target detection job | `find_target.u3p` | Name of the uniVision job for detecting calibration target | `update_reference_frame` subprogram |

### Calibration target

The calibration target must be set in the program for the following commands:
- `Calculate Calibration`
- `Calibrate Ground`
- `Calibrate Target`
- `Get Target Pose`

Update the calibration target in:
- `run_calibration` subprogram (at Calculate Calibration and Calibrate Ground)
- `update_reference_frame` subprogram

Add, remove or update the pose variables, then select the use case.

## Network Configuration

The network settings for the vision device are configured in the wenglor vision device CBun settings:

| Parameter | Default value | Description |
| --- | --- | --- |
| IP address | `192.168.100.1` | IP address of the Machine Vision Device |
| Port | `32006` | Communication port for the Machine Vision Device |

Configure these settings in the wenglor vision device configuration in the workcell.

> NOTE
>
> Also check that **Kassow Robots** is selected in the robot manufacturer drop-down of the robot server on the Machine Vision Device website (e.g. B60, MVC). See [Settings on Device Website](https://wenglor.github.io/robot-vision-generic-string/4_0_robot_vision_server/4_2_0_settings_on_device_website/) in the wenglor robot vision manual.
