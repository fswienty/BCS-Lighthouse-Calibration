# BCS-Lighthouse-Calibration
 
These scripts can be used to calibrate the lighthouse positioning system for use with the Crazyflie 2.1. They are supposed to help people working in the DroneLab at the BCS group at TU Darmstadt.

#### get_bs_position.py
Outputs the coordinates of the lighthouse base stations. The Vive headset has to be connected and SteamVR has to be running for the script to work. It seems to work best with the headset on the floor in the middle of the room facing the windows. The coordinates will look something like this:

```
{.origin = {-1.755063, -2.378910, 2.727174, }, .mat = {{0.569296, -0.795590, 0.207216, }, {0.750985, 0.605805, 0.262721, }, {-0.334551, 0.006050, 0.942358, }, }},
{.origin = {1.653693, 2.383405, 2.723262, }, .mat = {{-0.646577, 0.740935, -0.181529, }, {-0.676042, -0.666786, -0.313627, }, {-0.353419, -0.080062, 0.932033, }, }},
```

These coordinates have to be copy/pasted into the lighthouse.c file in the crazyflie firmware. Additionally, the lines 

```
#ifndef DISABLE_LIGHTHOUSE_DRIVER
 #define DISABLE_LIGHTHOUSE_DRIVER 1
#endif
```

have to be commented out to compile the firmware with lighthouse positioning enabled.

#### print_position.py
Connects to a drone and prints its position. Useful to check if everything is working correctly. (0, 0, 0) should be in the middle of the room. One unit should be more or less one meter. The script outputs the position every 500 ms for 10 s, but this can easily be changed.

#### autonomousSequence.py
Connects to a Crazyflie and makes it fly to a predefined sequence of points. If everythings works correctly, it should start, fly a square, and land. The Crazyflie should be close to (0, 0, 0) before executing this script.
