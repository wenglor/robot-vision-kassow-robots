# Kassow Robots Vision Manual

!!! note

    This manual focuses exclusively on Kassow Robots-specific topics. For general robot vision information, please refer to the [wenglor robot vision manual](https://wenglor.github.io/robot-vision-generic-string/).

This repository contains an example program to set up and start the generic vision interface to wenglor Machine Vision Devices on your Kassow robot.

The robot vision example for Kassow Robots consists of the following files:

- `wenglor_vision_1.1.0.kr2` — the example program file that demonstrates the vision interface usage
- `wenglor_vision_devices_1.1.0.cbun` — the CBun that provides the wenglor vision device node with API methods

!!! note

    The example was tested with the Robot Controller AC PROFINET, the robot arm KR0810 and the software version FireFly 4.1. The CBun and robot example program are compatible with the KR Series and Edge Edition and firmware FireFly.

---

## How the manual is organized

```mermaid
graph LR
    A[1. Installation & Setup] --> B[2. User Configuration]
    B --> C[3. Robot Program]
    C -.-> D[4. Troubleshooting]
    D -.-> E[5. Support & Feedback]
```

1. [Installation & Setup](1_0_0_installation.md) — install the required CBuns and configure the network connection to the Machine Vision Device.
2. [User Configuration](2_0_0_user_configuration.md) — adjust the workcell and program variables to your setup.
3. [Robot Program](3_0_0_robot_program.md) — how the example program's subprograms work together.
4. [Troubleshooting](4_0_0_troubleshooting.md) — common issues and how to resolve them.
5. [Support & Feedback](5_0_0_support_and_feedback.md) — where to report bugs or suggest features.

!!! note

    The generic robot vision API (commands, return values, error codes), the calibration guidelines, and the uniVision job setup are documented once in the [wenglor robot vision manual](https://wenglor.github.io/robot-vision-generic-string/4_0_0_robot_vision_server/) and are **not** repeated here. This manual only describes how the Kassow Robots example uses them.
