# Troubleshooting

## Insufficient Calibration Accuracy
You can improve calibration accuracy by using more than five calibration poses. Add additional calibration poses to the persistent `g_calib_poses` at the Workcell section.

## Communication Errors
- Verify, that the network setup of the added wenglor visiond device fits to your setup
-  Ensure the robot server on the vision device is active. Therefore navigate to the device website -> Jobs -> Processing Instance -> Robot Server.
- Check network connectivity/firewall
