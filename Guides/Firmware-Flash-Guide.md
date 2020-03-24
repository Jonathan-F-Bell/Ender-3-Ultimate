# Firmware Flash Guide

This guide will walk you through the steps of flashing new firmware to your Ender-3 to enable the use of a BLTouch.

**Note:** This guide assumes that you have already flashed a bootloader to your Ender-3. If you haven't, follow this guide _insert link_ to do so.

##### Materials/Software

* Ender-3 or Ender-3 Pro with bootloader flashed
* [Mini USB Cable (NOT Micro USB)](https://www.monoprice.com/product?p_id=3896)
* [Arduino IDE (NOT the web editor)](https://www.arduino.cc/en/Main/Software)
* Customized Marlin Firmware



##### What firmware should I use?

This guide comes with a customized Marlin firmware that has been configured to work on an Ender-3 with a BLTouch installed. This firmware includes the following changes from the stock firmware that ships on the Ender-3.

* Upgraded to Marlin 2.0.1
* Based on the Ender-3 configuration available from the Marlin project. This includes various optimizations to motor control and movement speeds.
* BLTouch used as Z-stop
* Define pin 27 as a servo for BLTouch use
* Set Nozzle to probe offset x and y to match that of the stock Creality kit bracket
* Disable min z software endstop to allow auto leveling to function
* Enable 4 point linear bed leveling
* Enable restore leveling after home
* Enable safe Z homing, which requires x and y to home first and then moves the nozzle to the center of the bed to prevent the z-probe from missing the bed
* Disable M503 command to save memory
* Disable EEPROM_CHITCHAT to save memory
* Enable slim lcd menus to save memory
* Disable the speaker to save memory, since we've detached it to install the BLTouch
* Disable printer info screen to save memory
* Enable show remaining time on current print
* Enable power loss recovery
* Enable smaller marlin boot logo to save memory
* Enable babystepping on z-probe offset
* Disable arc support to save memory
* Added a custom menu item to manually home and auto level the bed



### Flashing the Firmware

1. Download and install the Arduino IDE from [here](https://www.arduino.cc/en/Main/Software).
2. If you haven't already done so in previous guides, clone the repo to your computer or download it as a zip with [this link](https://github.com/Jonathan-F-Bell/Ender-3-Ultimate/archive/master.zip). Unzip the download.
3. Within the download, navigate to Ender-3-Ultimate -> Firmware -> Marlin and open the "Marlin.ino" Arduino file in the Arduino IDE. ![Marlin Folder Path](/Images/Photos/marlinFolder.png)
4. Next, we need to add board info for the Sanguino board used in the Ender-3 to the Arduino software. Navigate to the Arduino preferences from the menu bar and paste the following URL into the "Additional Boards Manager URLs" section - https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json ![Board URL Location](/Images/Photos/boardURL.png)
5. Click OK to close preferences.
6. In the Arduino menu bar, go to Tools -> Board -> Boards Manager... ![Boards Manager Menu](/Images/Photos/boardsManagerMenu.png)
7. In the Boards Manager window, search for "Sanguino" and click "Install", then close the Boards Manager. ![Board manager popup](/Images/Photos/boardManager.png)
8. In the Arduino menu bar, go to Tools -> Board and select "Sanguino" from the bottom of the boards list. ![Board selection menu](/Images/Photos/sanguinoBoardList.png)
9. In the Arduino menu bar, go to Tools -> Processor and select "ATmega1284 or ATmega1284P (16 MHz)" from the list. ![Processor select menu](/Images/Photos/processorSelect.png)
10. In the Arduino menu bar, go to Sketch -> Include Library -> Manage Libraries... ![Manage Library menu item](/Images/Photos/manageLibraryMenu.png)
11. In the Library Manager search for and install "U8glib". ![U8glib install](/Images/Photos/u8glib.png)
12. Make sure your Ender-3 is turned off and disconnected from power. 
13. Plug the Micro USB cable into your computer and the port on the front of your Ender-3.
14. Your Ender-3 should power up. If it doesn't, check the USB connection.
15. In the Arduino menu bar, go to Tools -> Port -> and select the port your printer is on. This is likely the only port that will show up. If you see multiple ports, unplug any other serial devices from your computer (Arduinos, firmware flashers, Raspberry Pis, etc.) and try again. ![Port select menu](/Images/Photos/portSelect.png)
16. Click the forward arrow in the top left of the Arduino IDE. This will compile and upload the firmware. ![Upload firmware button](/Images/Photos/uploadFirmware.png)
17. Wait until the progress bar finishes and the Arduino IDE says "Done Uploading". ![Done uploading screen](/Images/Photos/doneUploading.png)
18. Your printer should now begin to boot into its new firmware. It is now safe to unplug the USB cable, reconnect your printer to power, and turn it on normally.
19. Before using your BLTouch equipped printer, you MUST configure the z-offset of the BLTouch or your printer WILL crash or print poorly. [This guide](/Guides/BLTouch-Config-Guide.md) will walk you through the steps to configure the z-offset and other refinements.





