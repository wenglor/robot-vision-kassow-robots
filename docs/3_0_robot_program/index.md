# Robot Program

## The wenglor device node
With the wenglor device you have access to all method calls of the robot vision API (see [chapter 4.6 Generic Robot Vision API](https://wenglor.github.io/wenglor-robot-vision/4_0_robot_vision_server/4_6_0_generic_robot_vision_api/)). 


<img src="images/17%20program%20-%20command%20overview.png" alt="wenglor_node_command_overview" class="big"/>

All methods of the wenglor node provide a test option that executes the method without the need of a robot program. To execute the method, in this case a job change, enter the desired job name and hit the play button.

<img src="images/18%20program%20-%20run%20or%20test%20functions.png" alt="execute_command_with_play_button" class="big"/>

## Update the example program

The robot example program uses the methods and is prepared that only small adjustments are necessary. 
Update the calibration target in the following two commands:

- Calculate Calibration
- Calibrate Ground

At the command `Calculate Calibration`, update the calibration target in the `run_calibration` subprogram.

<img src="images/19%20program%20-%20adjust%20calibration%20target%20-%20calculate%20calibration.png" alt="select_calibration_target_at_calculate_calibration" class="big"/>

At the command `Calculate Ground`, update the calibration target in the `run_calibration` subprogram at the second calibration step if the camera is not mounted on the robot.

<img src="images/20%20program%20-%20adjust%20calibration%20target%20-%20calibrate%20ground.png" alt="select_calibration_target_at_calibrate_ground" class="big"/>

Update the uniVision job names. The example contains the following default uniVision job names:

- Calibration job: calibration.u3p
- Detection of objects: find_objects.u3p

Use the same job names in uniVision or update the job names in the robot program at the following places:

- At the beginning of the subprogram `run_calibration`.
- At the end of the subprogram `prepare_detection`.

<img src="images/21%20program%20-%20adjust%20calibation%20job.png" alt="update_job_at_run_calibration" class="big"/>

Update the detection job at the end of the subprogram `prepare_detection`.

<img src="images/22%20program%20-%20adjust%20detection%20job.png" alt="update_job_at_prepare_detection" class="big"/>

## Set Payload and TCP

Set payload and update TCP via:

- Updating the system variables
- Creating variables that are assigned to the system variables within the program

In case of multiple tools, create a variable for each tool and assign it, when the tool is changed. At the beginning of the program, add those two commands.

<img src="images/24%20program%20-%20init%20payload%20and%20tcp.png" alt="set_payload_and_tcp" class="medium"/>

## Run the program

|Subprogram name| Details|
|---------------|--------|
| prepare_detection | Checks the camera state for errors and the calibration state. In case of no available calibration, it calls the run_calibration subprogram. After the calibration program, it checks the state again to see if the calibration was successful. If not, the program quits. Otherwise, the detection job is loaded. |
| single_detection | Calls prepare_detection first. <br><br> Triggers a detection and moves the robot in a linear movement to the object. Even in case of multiple found objects, the subprogram only moves to one object. |
| multi_detection | Calls prepare_detection first. <br><br> Triggers a detection and moves the robot to all objects. The movement will take place from one object to the next one, until no further object is available.<br><br> At first, it checks the number of found objects. Then it iterates through the object information via an index accessor. |
| run_calibration | Loads the calibration job, clears the temporary calibration data (not the calibration itself) and moves the robot to the calibration poses. Then it calculates the calibration. If the camera is not mounted on the robot, it performs the second calibration step to calibrate the camera to object ground level. At the end, it calls validate_calibration. |
| validate_calibration | Checks the calibration results by moving the robot TCP to the bottom left corner of the calibration target. As the camera is not triggered again, it is important that the calibration target was not moved between the calibration and the validation. <br><br> For safety reasons, enter a safety offset before the actual movement. This safety offset shifts the target pose above the calibration target. |

Select the subprogram to execute.

<img src="images/23%20program%20-%20call%20subprogram.png" alt="select_subprogram" class="big"/>



