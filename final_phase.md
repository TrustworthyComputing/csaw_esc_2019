# Final Phase

Welcome to the finals phase for CSAW ESC'19! This document will discuss more about the finals and how to install and utilize the provided RFID board. There is one simple rule for solving the challenges:

1. **Your solution should work using the provided, unmodified firmware**. Essentially, this means that installing a modified version of the firmware on the board to solve the challenge will not receive any credit at the finals. All challenges should be solved using the inputs from the board. During the challenge finals, the judges and challenge organizers will verify the challenge solutions of the teams on a separate RFID board that is programmed with the same firmware provided to the contestants that has not been modified.

## Challenge Structure Overview

Throughout the next few weeks **several challenge sets will be released**. Each set will contain independent challenges for the teams to solve and all points from all challenges will be accumulated in the final score of each team. Challenges will be given a different number of points based upon their difficulties; the number of points for each challenge is revealed once the challenge is solved.

## Hardware Overview

This year, we have prepared a custom designed RFID system for the competition. Each team will receive:

* One (1) RFID board

* One (1) White RFID card
	* This card is fully programmable using the provided RFID system.

* One (1) Blue RFID fob
	* You should only use this if explicitly instructed by a challenge, otherwise always use the white card.

![alt text][boardDescription]

### Hardware FAQ

In case you encounter any of the following, please refer to the recommended resolutions:

*  *RFID Fail:* This issue is caused by trying to scan the RFID card too quickly.
	*  *Resolution:* The RFID card must be placed near the reader for about two seconds. The reader must read/write each sector of the card. This can take some time.

*  *Double Pressing:* Pressing the Cycle 'A' button also triggers the cycle challenge button.
	*  *Resolution:* The dark blue RFID reader on the back of the white PCB board needs to have a few degrees offset from the parallel position to minimize interference. To ensure this is the case, you may need to gently bend the RFID reader *away* from the PCB to ensure the former is just a few degrees offset.

## Installing and Programming the RFID Board

Periodically, new challenge sets will be released in separate binaries. These binaries will be in a zipped file which will contain the corresponding board firmware, and a script for flashing the firmware to the board. To flash the boards, we provide a virtual machine with all necessary configurations pre-installed:

1. First install VMWare Player [newest version (15.5)](https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0|PLAYER-1550|product_downloads) or the [legacy version for any compatibility issues](https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/14_0|PLAYER-1417|product_downloads).

2. After the Player is installed, use File->open and select the provided VM file.  

![alt text][openVM]

3. Select to ‘Play’ the VM.

4. If prompted as to whether the VM was copied or moved, select ‘I copied it’.

5. At the login screen enter the password `esc`

6. Use a micro-USB cable to connect the RFID board into your system. *Please ensure the micro-USB cable you are using is a data cable, not a charge-only cable.* Then, select the RFID board within 'Removable Devices' and connect it to the VM.  

![alt text][connectTeensy]

7. Open the file explorer and navigate to Downloads -> RFID programmer.

![alt text][openFiles]

8. Right click in the window and select ‘Open in Terminal’.

![alt text][loadTerminal]

9. Run `./avrLoader.sh`

![alt text][runLoader]

10. The programmer will run and eventually complete.

![alt text][loaderProgress]

11. If the above screen doesn’t appear, the device may have disconnected while reprogramming. Simply reconnect it to the VM using step 6 (it may appear under a slightly different name) and rerun the script.

12. When new challenge sets are released, they will be provided in a new zip file. Simply download this file to the host machine or from within the VM. If downloading from a host PC, simply drag and drop the zip file into the VM.  

![alt text][dragDrop]

13. Unzip the new files, navigate inside and run the corresponding loader script.

## Programming the RFID card

To complete the challenges it is necessary to load specific values to the RFID card. We provide a script to assist with this:

1. Open the provided VM and navigate to the Downloads folder.

2. Open the `sender.py` program.

3. Set the correct values of the RFID card based on your solution to the challenge.

![alt text][progRFID]

4. Open a terminal in the downloads folder and run the command `python3 sender.py`

5. Upon running the program, the OLED screen on the PCB will indicate that it is ready to program the RFID card. The Python program will also output a hash value of the sent data.

![alt text][progRFIDTerm]

6. Use the *white* RFID card (unless explicitly asked to do otherwise by a challenge) and slowly bring it close to the blue RFID reader/writer on the back of the board. The orange status LED light on the Teensy will change from flashing to solid. This will indicate that the RFID reader is busy. Upon completion, the onboard OLED screen will indicate whether the program succeeded or failed. If it failed, it will return the user to the 'ready to program' state.
	* Programming a card takes a couple seconds. If you move the card too quickly, it is possible that the card programming operation will fail, so it should be repeated slowly.

## Solving a Challenge

1. When you have identified the solution to a challenge, you can program the RFID card as above.

2. Each time, you should edit `sender.py` and ensure the values of A and B are correct into the program (as shown in the image below):  

![alt text][hash]

3. The `sender.py` program will print out a hash of the RFID card values as well as A and B. You should treat this value is the `flag` for each challenge and you should include it in your final report when discussing challenge solutions, to help the organizers verify your challenge solutions.

4. Note that the aforementioned hash is sensitive to every bit of the input. Thus, you need to ensure the following are correct when setting each input to the card:
	* Only set the values for the RFID card that you are utilizing in the challenge and *all other locations should be set to 0*. This is necessary, as having extra values set to non-zero will generate a hash for that challenge that will not be correct.
	* If you use A and B in a challenge, their values (0x0 – 0xF) must be set correctly in `sender.py`. If A and B are not uses, they must be set to 0 in `sender.py`.

5. The board will inform you whether the challenge has been solved correctly using the provided inputs, and also report the number of points corresponding to that challenge. The board will not accumulate your total points (the challenge leaders will verify your solutions on a separate board).
  

## Submitting Results in the Final Report

When submitting the final report, each team should also upload a zip file with the corresponding `sender.py` programs used for each challenge. Each copy of the program should pertain to a single challenge only and should be renamed accordingly to clearly reflect which challenge it corresponds to. These files will be used to verify that a team solved a challenge correctly at the time of report submission. Note that the generated hash value for each challenge you solved correctly should also be included in the final report.


[connectTeensy]: https://imgur.com/B6ptFjs.png  "Connect Device"
[dragDrop]: https://imgur.com/rpmwmRf.png  "Drag and Drop"
[hash]: https://imgur.com/mxSXqOi.png  "Hash"
[loaderProgress]: https://imgur.com/zQOkSXB.png  "Loader Progress"
[loadTerminal]: https://imgur.com/4vzSmQN.png  "Loading Terminal"
[openFiles]: https://imgur.com/DPrifve.png  "Open File Explorer"
[openVM]: https://imgur.com/alydCyV.png.png  "Open Virtual Machine"
[progRFID]: https://imgur.com/Guef6iV.png  "Programming RFID"
[progRFIDTerm]: https://imgur.com/SjhgFqN.png  "Programming RFID Terminal"
[runLoader]: https://imgur.com/EKnOwOc.png  "Run Binary Loader"
[boardDescription]: https://imgur.com/cWIpbIh.png  "Board Description"
