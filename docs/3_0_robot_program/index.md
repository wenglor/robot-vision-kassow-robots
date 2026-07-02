# Robot Program

## The wenglor device node
With the wenglor device you have access to all method calls of the robot vision API (see [chapter 4.6 Generic Robot Vision API](https://wenglor.github.io/wenglor-robot-vision/4_0_robot_vision_server/4_6_0_generic_robot_vision_api/)). 


<img src="images/17%20program%20-%20command%20overview.png" alt="wenglor_node_command_overview" class="big"/>

All methods of the wenglor node provide a test option that executes the method without the need of a robot program. To execute the method, in this case a job change, enter the desired job name and hit the play button.

<img src="images/18%20program%20-%20run%20or%20test%20functions.png" alt="execute_command_with_play_button" class="big"/>

## Update the example program

The robot program requires small adjustments depending on the use case.

### Update the calibration target

The following commands require the input of the calibration plate:

- `Calculate Calibration`
- `Calibrate Ground`
- `Calibrate Target`
- `Get Target Pose`

In the robot example program, the calibration target must be set in the `run_calibration` subprogram.

<img src="images/19%20program%20-%20adjust%20calibration%20target%20-%20calculate%20calibration.png" alt="select_calibration_target_at_calculate_calibration" class="big"/>

Set the calibration target at the second calibration step if the camera is not mounted on the robot (in `run_calibration`).

<img src="images/20%20program%20-%20adjust%20calibration%20target%20-%20calibrate%20ground.png" alt="select_calibration_target_at_calibrate_ground" class="big"/>

Set the calibration target in the `update_reference_frame` subroutine as well.

### Update the uniVision job names

By default, the following uniVision job names are used:

- Calibration job: `calibration.u3p`
- Detection of objects: `find_objects.u3p`
- Detection of calibration target: `find_target.u3p`

If using different uniVision job names, make sure to update them in the program:

- At the beginning of the subprogram `run_calibration`.
- At the `single_detection` subroutine.
- At the `multi_detection` subroutine.
- At the `update_reference_frame` subroutine.

<img src="images/21%20program%20-%20adjust%20calibation%20job.png" alt="update_job_at_run_calibration" class="big"/>

<img src="images/22%20program%20-%20adjust%20detection%20job.png" alt="update_detection_job" class="big"/>

## Set Payload and TCP

Set payload and update TCP via:

- Updating the system variables
- Creating variables that are assigned to the system variables within the program

In case of multiple tools, create a variable for each tool and assign it when the tool is changed. At the beginning of the program, add those two commands.

<img src="images/24%20program%20-%20init%20payload%20and%20tcp.png" alt="set_payload_and_tcp" class="medium"/>

## Run the program

After configuration, run the program. Several dialogs guide you through the process. The example program is just an example — adjust it to your needs.

| Subprogram name | Details |
|-----------------|---------|
| `calibrate_if_needed` | Checks the camera state for errors and the calibration state. In case of no available calibration, it calls the `run_calibration` subprogram. After the calibration program, it checks the state again to see if the calibration was successful. |
| `single_detection` | Calls `calibrate_if_needed` first. <br><br> Loads the detection job, moves the robot to the detection pose and triggers the object detection. After this, the robot moves in a linear movement to the object. Even if multiple objects are detected, the subprogram will only move to one object. |
| `multi_detection` | Calls `calibrate_if_needed` first. <br><br> Loads the detection job, moves the robot to the detection pose and triggers the object detection. Then it iterates through the object information via an index accessor and moves the robot to all of the objects. |
| `update_reference_frame` | Calls `calibrate_if_needed` first. Loads the `find_target` job and moves the robot to the pose where the camera can see the calibration target. Then it detects the calibration target pose and writes it into the persistent `g_reference_frame` variable. If the poses in the machine related to the reference frame are not taught yet, the program will stop. If you execute the subroutine again after setting `WU_MACHINE_POSES_TAUGHT`, it will also move to the updated poses in the machine. You need to add your poses at the bottom of this subroutine. |
| `run_calibration` | Loads the calibration job, clears the temporary calibration data (not the calibration itself) and moves the robot to the calibration poses. Then it calculates the calibration. If the camera is not mounted on the robot, it performs the second calibration step to calibrate the camera to object ground level. |
| `validate_calibration` | Checks the calibration results by moving the robot TCP to the bottom left corner of the calibration target. As the camera is not triggered again, it is important that the calibration target was not moved between the calibration and the validation. <br><br> For safety reasons, enter a safety offset (in mm) before the actual movement. This safety offset shifts the target pose above the calibration target. |

Select the subprogram to execute.

<img src="images/23%20program%20-%20call%20subprogram.png" alt="select_subprogram" class="big"/>
