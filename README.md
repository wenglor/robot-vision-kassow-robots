# Example Kassow Robots program files for the generic vision interface

**Version:** 1.1.0

This repository demonstrates how to use the Generic Vision Interface with wenglor vision devices on a Kassow robot. The included `.kr2` program file and `.cbun` form a working sample program that you can adopt and customize for your application.

> NOTE
>
> This repository focuses exclusively on Kassow Robots-specific topics. For general robot vision information, please refer to the [wenglor robot vision manual](https://wenglor.github.io/robot-vision-generic-string/).

📖 **Full documentation** is available in the [online manual](https://wenglor.github.io/robot-vision-kassow-robots/)

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Sample Program](#running-the-sample-program)
- [Troubleshooting](#troubleshooting)
- [Support & Feedback](#support--feedback)

---

## Prerequisites

> Tested with Robot Controller AC PROFINET, robot arm KR0810, and software version FireFly 4.1

- Kassow Robots KR Series or Edge Edition with FireFly firmware
- Basic knowledge of Kassow Robots programming
- [B60](https://www.wenglor.com/en/Machine-Vision/Smart-Cameras-and-Vision-Sensors/Smart-Camera-B60/c/cxmCID221375) (firmware >= 1.4) or [Machine Vision Controller (MVC)](https://www.wenglor.com/en/Machine-Vision/Machine-Vision-Controllers/c/cxmCID221381) (firmware >= 1.1)
- A [uniVision](https://www.wenglor.com/en/Machine-Vision/Machine-Vision-Software/Image-Processing-Software-uniVision-3/c/cxmCID222459) job for calibration and object detection
- Network connection between robot controller and vision device

---

## Installation

1. Get the files from the [sources](sources) directory.
2. Install the required CBuns:
   - `System Utils` for Program Control
   - `wenglor vision devices`
3. Copy the example program to the robot controller.

For detailed installation steps, see the [Installation & Setup documentation](https://wenglor.github.io/robot-vision-kassow-robots/1_0_installation/).

---

## Configuration

The robot program requires configuration of:

- **Network settings**: IP address and port of the vision device
- **Calibration poses**: Minimum of 5 poses for hand-eye calibration
- **uniVision job names**: Calibration, detection, and target detection jobs
- **Use case**: Camera mounted on robot or not
- **Workcell variables**: Persistent variables for detection pose and reference frame

For detailed configuration steps, see the [User Configuration documentation](https://wenglor.github.io/robot-vision-kassow-robots/2_0_user_configuration/).

---

## Running the Sample Program

1. Load the program [wenglor_vision_1.1.0.kr2](sources/wenglor_vision_1.1.0.kr2) on your robot.
2. Configure the required variables and poses.
3. Select the subprogram to execute:
   - `calibrate_if_needed`: Checks calibration state and runs calibration if needed
   - `single_detection`: Detects and moves to a single object
   - `multi_detection`: Detects and moves to all objects
   - `update_reference_frame`: Updates reference frame for mobile platforms
4. Execute the program and monitor the messages on the robot controller display.

For detailed program information, see the [Robot Program documentation](https://wenglor.github.io/robot-vision-kassow-robots/3_0_robot_program/).

---

## Troubleshooting

### Communication Errors

- Verify IP/port configuration in the program
- Ensure the robot server on the vision device is active
  - Go to the device website → Jobs → Processing Instance → Robot Server
- Check network connectivity and firewall settings

### CBun Installation Issues

- Ensure System Utils CBun is installed and Program Control is activated
- Verify the wenglor vision devices CBun is properly installed from USB stick
- Check that the wenglor vision device is activated in the workcell

### Calibration Issues

- Ensure a minimum of 5 calibration poses is taught
- Verify calibration target is correctly set in the program
- Check that the camera is properly positioned for the use case

For more troubleshooting information, see the [Troubleshooting documentation](https://wenglor.github.io/robot-vision-kassow-robots/4_0_troubleshooting/).

---

## Support & Feedback

- **Bugs:** Please open a new Issue in the [GitHub Issues section](../../issues) if needed.
- **Feature Requests & Ideas:** Discuss suggestions in the Discussions → Ideas category under [GitHub Discussions](../../discussions).