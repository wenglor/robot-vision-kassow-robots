# Installation & Setup

The Kassow robot vision example requires installing specific CBuns (Custom Bundles) and configuring the network connection to the Machine Vision Device.

## Supported controllers

| Controller | Minimum software version | Notes |
| --- | --- | --- |
| KR Series | FireFly 4.1 | Tested with Robot Controller AC PROFINET and KR0810 |
| Edge Edition | FireFly | Compatible with the CBun and example program |

## Files

Download the robot example from this [GitHub repository](https://github.com/wenglor/robot-vision-kassow-robots/tree/main/sources/). It consists of:

- `wenglor_vision_1.1.0.kr2` — the example program file that demonstrates the vision interface usage
- `wenglor_vision_devices_1.1.0.cbun` — the CBun that provides the wenglor vision device node with API methods

## CBun Installation

Install the relevant CBuns in order to use the robot example program:

- `System Utils` for `Program Control`
- `wenglor vision devices`

## System Utils for Program Control

In the robot example program, the System Util CBun is required in order to exit the program execution if some conditions are not met.

Navigate to the CBun view to add or remove CBuns.

<img src="images/01%20main%20-%20navigate%20to%20cbun%20screen.png" alt="navigate_to_cbuns_install" class="medium"/>

Click on the + icon to install a CBun.

<img src="images/02%20cbuns%20-%20add%20cbun.png" alt="add_cbun_screen" class="small"/>

Install `system_utils`. It should be available on the robot controller. Otherwise, contact your Kassow Robots partner.

<img src="images/03%20cbuns%20-%20install%20cbun%20system_utils.png" alt="install_system_utils" class="medium"/>

Add the method Program Control from the System Utils CBun.

<img src="images/04 cbuns - add program control from system utils.png" alt="select_program_control" class="medium"/>

Activate the Program Control Custom Device with its default configuration.

<img src="images/05%20workcell%20-%20acticate%20program%20control.png" alt="activate_program_control" class="big"/>

## wenglor CBun

Download the latest wenglor CBun version from this [GitHub repository](https://github.com/wenglor/robot-vision-kassow-robots/tree/main/sources/) and put the files on a freshly formatted stick.

Plug in the USB stick in the robot controller. Click on Robot -> SHARED to install the wenglor CBun from the USB stick.

<img src="images/06%20cbuns%20-%20navigate%20to%20shared%20volume.png" alt="select_usb_stick_as_source" class="small"/>

Select `wenglor_vision_devices` to install it.

<img src="images/07%20cbuns%20-%20wenglor%20cbun%20on%20shared%20volume.png" alt="select_wenglor_vision_devices" class="small"/>

Click on the + icon to add the wenglor vision device.

<img src="images/08%20cbuns%20-%20add%20wenglor%20device.png" alt="add_wenglor_vision_device" class="big"/>

Activate the wenglor vision device in order to initiate a connection from the robot controller to the vision device.

<img src="images/09%20workcell%20-%20custom%20devices%20wenglor%20selected.png" alt="wenglor_vision_device_selected" class="big"/>

In case of a valid network configuration to the Machine Vision Device, the device is activated successfully.

> NOTE
>
> - The connection is only maintained during the program execution. So the Workcell state might become outdated.
> - Check the status for the robot connection on the device website of the Machine Vision Device (Tab `Jobs` -> `Robot Server`, see [chapter 4.2 Settings on Device Website](https://wenglor.github.io/robot-vision-generic-string/4_0_robot_vision_server/4_2_0_settings_on_device_website/)).

<img src="images/10%20workcell%20-%20custom%20devices%20wenglor%20activated.png" alt="wenglor_vision_device_activated" class="big"/>

## Network configuration

Configure the network settings of the Kassow robot controller so it can reach the Machine Vision Device (by default `192.168.100.1`).

Ensure that:
- The robot controller and vision device are on the same network
- The IP address of the vision device is accessible from the robot controller
- No firewall rules block the communication (default port: `32006`)

> NOTE
>
> On the Machine Vision Device website (Tab `Jobs` → `Robot Server`), make sure the robot server is active and the robot manufacturer is set to **Kassow Robots**. See [Settings on Device Website](https://wenglor.github.io/robot-vision-generic-string/4_0_robot_vision_server/4_2_0_settings_on_device_website/) in the wenglor robot vision manual.

## Loading the program

After installing the CBuns and configuring the network, load the example program `wenglor_vision_1.1.0.kr2` from the USB stick to the robot controller. The program is then ready to be configured and executed.

For configuration details, see [User Configuration](../2_0_user_configuration/index.md).