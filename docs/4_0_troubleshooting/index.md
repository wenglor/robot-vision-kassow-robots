# Troubleshooting

## Insufficient Calibration Accuracy
You can improve calibration accuracy by using more than five calibration poses. Add additional calibration poses to the `WU_CALIB_POSES` program variable.

- Ensure minimum of 5 calibration poses are taught
- Verify calibration target is correctly set in the program
- Check that the camera is properly positioned for the use case

## Communication Errors
- Verify that the network setup of the added wenglor vision device matches your setup.
- Ensure the robot server on the vision device is active. Navigate to the device website → Jobs → Processing Instance → Robot Server.
- Check network connectivity/firewall

## CBun Installation Issues
- Ensure System Utils CBun is installed and Program Control is activated
- Verify the wenglor vision devices CBun is properly installed from USB stick
- Check that the wenglor vision device is activated in the workcell
