# BLTouch Config Guide

This guide will walk you through the steps of configuring a BLTouch equiped Ender-3 running Marlin 2.x.x

##### Materials

* Ender-3 or Ender-3 Pro
* 1 Sheet of standard computer paper



### A. Setting the Z-Offset

1. Power on your Ender
2. Click the dial to enter the menu, scroll to "Motion", and select it. ![Motion Menu](/Images/Photos/motion.jpg)
3. Scroll to "Auto Home" and select it. ![Auto Home Menu](/Images/Photos/autoHome.jpg)
4. Wait for the printer to finish auto homing. It should complete with the head positioned above the center of the bed.
5. Re-enter the menu, scroll to "Motion", select it, and then select "Move Axis". ![Move Axis Menu](/Images/Photos/moveAxis.jpg)
6. Scroll to "Move Z" and select it. ![Move Z Menu](/Images/Photos/moveZ.jpg)
7. Scroll to "Move 1mm" and select it. ![Move 1MM Menu](/Images/Photos/move1MM.jpg)
8. Rotate the knob until the head is close to the bed. It does not need to be touching, we will fine tune it in the next step. **WARNING**: Be careful not to move the knob too fast. If you spin it quickly, the printer will attempt to move to a value that is outside its range and you will crash the head. If this happens, power off the printer immediatly to prevent damage. ![Head Distance Photo](/Images/Photos/headDistance1.jpg)
9. Click to exit the 1mm menu. In the Move Z Axis menu, scroll down to and select "Move 0.025mm". ![Move 0.025MM Menu](/Images/Photos/move025MM.jpg)
10. Place a sheet of printer paper between the nozzle and the bed. Use the knob to slowly move the head downwards until the head is just barely rubbing against the sheet of paper. ![Paper Test](/Images/Photos/paper.jpg)
11. Write down the value that is on the screen. It will be something like -2.250, but WILL be different for every printer and BLTouch. This is your z-offset. ![Z-Offset](/Images/Photos/zOffset.jpg)
12. Use one of the faster movement settings (like 1mm or 10mm) to move the head up off the bed to avoid hitting the bed in the next step.
13. From the main screen, click the dial to enter the menu and then select "Configuration". _configMenu img_
14. From the configuration menu, select "Probe Z Offset". ![Probe Z Offset Menu](/Images/Photos/probeZOffset.jpg)
15. Take note of the number displayed on screen. If it is zero, you can continue to the next step. If it is not zero, add this number to the z-offset value we found earlier. This is your new z-offset value. For example, if my screen displayed -1.000 and my z-offset was -2.250, my new z-offset value would be -3.250.
16. Spin the dial until the value on screen is your z-offset value. **Note**: This will take a lot of spinning. Unfortunatly the only way to have a more accurate z-offset setting is to make the increment very low.
17. Click the dial to select your newly entered value.
18. On the Configuration screen you are returned to, select "Store Settings". Note that nothing visible will happen, but clicking this button stores your new z-offset into EPROM so that it will survive a power cycle. ![Store Settings Item](/Images/Photos/storeSettings.jpg)
19.  Return to the main menu, scroll to, and select "Bed Leveling". ![Bed Leveling Item](/Images/Photos/bedLeveling.jpg)
20. Select "Home & Bed Level" and wait for the printer to complete its initial home and bed level. ![Home and Level Item](/Images/Photos/homeAndLevel.jpg)
21. Once your printer has finished leveling, you are ready to print! You should run a Home & Bed Level from time to time to account for shifts in the bed over time. 