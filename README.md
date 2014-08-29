Installing Garcad's hotend on a RigidBot
===============

# Hardware

1. Connect MAX6675 board to RigidBoard
   * +5V -> +5V

![RigidBoard](/img/rigidboard.png)
![MAX6675](/img/MAX6675.png)


# Software

1. Install prerequisite software
   * Windows: http://arduino.cc/en/Guide/Howto
   * Linux:   http://arduino.cc/en/Main/FAQ#linux


2. Grab the following repository:
   
   https://github.com/karl-nilsson/Marlin/archive/Marlin_v1.zip

3. Open with Arduino IDE

4. Navigate to Configuration.h
   * if you have a RigidBot Big, uncomment line #6
   * if you have a dual extruder, uncomment line #7

5. Select the correct options
   * Tools -> Board -> Arduino Mega 2560 or Mega ADK
   * Tools -> Serial Port -> (/dev/ACM0 on linux or /dev/COM# on windows)

6. Verify and Upload firmware
http://rollertrol.com/RollerNode/program/Arduino-blink-test-program-upload-296x194.jpg

# Printer Control

The RigidBoard uses a baud rate of 115200, so be sure to 
Additionally, you can use the Arduino IDE to watch the serial connection. Tools -> Serial Monitor. Make sure the baud rate is set correctly (dropdown box in lower-right hand corner)



# Caveats/Details/Etc.

Unfortunately, the RigidBoard does not play nicely with the 6675 board. For reasons unknown, the SS pin is tied to 5V, so standard SPI becomes impossible (we use the MOSI pin instead). Additionally, the 6675 board does not currently work in conjunction with the LCD addon. Finally, the Marlin codebase does not currently support multiple thermocouple amplifiers, so dual hotends won't work.
