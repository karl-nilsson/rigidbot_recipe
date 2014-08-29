Installing Garcad's hotend on a RigidBot
===============

# Hardware

1. Using a set of female-female jumper cables, connect MAX6675 board to RigidBoard
   * Use either the ICSP header, or the LCD header
   * Connect like colors (e.g. VCC -> VCC, MISO -> MISO, etc...)  

   ![RigidBoard](/img/rigidboard.png)
   ![MAX6675](/img/MAX6675.png)

2. Cut a 6" length of heavy-gauge wire to use as the heater cable

3. Solder the heater cable to the extruder board as indicated in the photograph.
  * polarity doesn't matter
  * if necessary, use a hot glue gun to insulate the connections

  ![heater connection](/img/heater_connx.jpg)

4. Connect the heater wires to the solderless terminals, and connect them to the hotend posts


# Software

1. Install prerequisite software
   * Windows: http://arduino.cc/en/Guide/Howto
   * Linux:   http://arduino.cc/en/Main/FAQ#linux


2. Grab the following repository:
   
   https://github.com/karl-nilsson/Marlin/archive/Marlin_v1.zip

3. Extract zip file and open "Marlin/Marlin.ino" (this should launch the Arduino IDE)

4. Navigate to Configuration.h
   * if you have a RigidBot Big, uncomment line #6
   * if you have a dual extruder, uncomment line #7

5. Select the correct options
   * Tools -> Board -> Arduino Mega 2560 or Mega ADK
   * Tools -> Serial Port -> (/dev/ACM0 on linux or /dev/COM# on windows)

6. Verify and Upload firmware

   ![arduino upload icon](http://rollertrol.com/RollerNode/program/Arduino-blink-test-program-upload-296x194.jpg)

# Printer Control

* The RigidBoard uses a baud rate of 115200, change settings as necessary
* Use the Arduino IDE's serial monitor as a debugging tool
  * Tools -> Serial Monitor (alternatively, CTRL+SHIFT+M)
  * 115200 Baud (lower-right hand corner)
  * Use the input box at the top of the window to send commands (i.e. [GCode][http://reprap.org/wiki/Mendel_User_Manual:_RepRapGCodes])



# Caveats/Details/Etc.
There are a number of quirks in the RigidBoard Design:
  * The ICSP headers are reversed
  * The SS pin is tied to +5V (making standard SPI impossible)
  * The 6675 board does not currently work in conjunction with the LCD addon.

Additionally, the Marlin codebase does not currently support multiple thermocouple amplifiers, so dual hotends won't work.

The RigidBoard image comes courtesy of Dennis Brown
https://plus.google.com/u/0/102831253296337169949/posts/eyavMevqVBF

