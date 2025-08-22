# Installation of CBuns

Install the relevant CBuns in order to use the robot example program:

- `System Utils` for `Program Control` and `Inverse Kinematics`
- `wenglor vision devices`

## System Utils for Program Control and Inverse Kinematics

In the robot example program, the System Util CBun is required in order to exit the program execution if some conditions are not met.

Navigate to the CBun view to add or remove CBuns.

<img src="images/01%20main%20-%20navigate%20to%20cbun%20screen.png" alt="navigate_to_cbuns_install" class="medium"/>

Click on the + icon to install a CBun.

<img src="images/02%20cbuns%20-%20add%20cbun.png" alt="add_cbun_screen" class="small"/>

Install `system_utils`. It should be available on the robot controller. Otherwise, contact your Kassow partner.

<img src="images/03%20cbuns%20-%20install%20cbun%20system_utils.png" alt="install_system_utils" class="medium"/>

Add the methods Program Control and Inverse Kinematics from the System Utils CBun.

<img src="images/04%20cbuns%20-%20add%20program%20control%20and%20inverse%20kinematics%20from%20system%20utils.png" alt="select_program_control_and_inverse_kinematics" class="medium"/>

Activate the Program Control Custom Device with its default configuration.

<img src="images/05%20workcell%20-%20acticate%20program%20control.png" alt="activate_program_control" class="big"/>

Activate the IK Custom Device with its default configuration.

<img src="images/06%20workcell%20-%20acticate%20inverse%20kinematics.png" alt="activate_inverse_kinematics" class="big"/>

## wenglor CBun

Download the latest wenglor CBun version from this [GitHub repository](https://github.com/wenglor/wenglor-kassow-vision/tree/main/sources/) and put the files on a freshly formatted stick.

Plug in the USB stick in the robot controller. Click on Robot -> SHARED to install the wenglor CBun from the USB stick.

<img src="images/07%20cbuns%20-%20navigate%20to%20shared%20volume.png" alt="select_usb_stick_as_source" class="small"/>

Select `wenglor_vision_devices` to install it.

<img src="images/08%20cbuns%20-%20wenglor%20cbun%20on%20shared%20volume.png" alt="select_wenglor_vision_devices" class="small"/>

Click on the + icon to add the wenglor vision device.

<img src="images/09%20cbuns%20-%20add%20wenglor%20device.png" alt="add_wenglor_vision_device" class="big"/>

Activate the wenglor vision device in order to initiate a connection from the robot controller to the vision device.

<img src="images/10%20workcell%20-%20custom%20devices%20wenglor%20selected.png" alt="wenglor_vision_device_selected" class="big"/>

In case of a valid network configuration to the Machine Vision Device, the device is activated successfully.

> NOTE
>
> - The connection is only maintained during the program execution. So the Workcell state might become outdated.
> - Check the status for the robot connection on the device website of the Machine Vision Device (Tab `Jobs` -> `Robot Server`, see [chapter 4.2 Settings on Device Website](https://wenglor.github.io/wenglor-robot-vision/4_0_robot_vision_server/4_2_0_settings_on_device_website/)).

<img src="images/11%20workcell%20-%20custom%20devices%20wenglor%20activated.png" alt="wenglor_vision_device_activated" class="big"/>