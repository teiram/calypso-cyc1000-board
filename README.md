# The calypso board project

Calypso is just another middleboard based on the Arrow/Trenz cyc1000 board. This was born as a personal project to experiment with such board as it was delivered by Arrow Electronics as part of their European "Jump Start" Program for FPGAs.

The board takes ideas and design from other existing hobbyist project boards, embracing the following design principles:
- Doesn't try to support multiple FPGAs and/or MCUs. it's based on the CYC1000 board and an R2040 as MCU
- Follows the Mist ideas about IO, being the MCU the hub for most IO needs. This is convenient since the CYC1000 doesn't expose a big number of pins to the outside world.
- Tries to be compatible to some extent with Mist IO, therefore exposing a SPI bus mastered by the MCU to the FPGA, and the well known select signals CONF_DATA0, MIST_SS2, MIST_SS3 and MIST_SS4. This should ease the task of porting cores from Mist or boards with a similar design.
# Features
- VGA444 output via an standard VGA DB15 connector
- Optional AV output via a RCA connector. Both VGA and AV share FPGA pins.
- DB9 connector for a joystick with up to 2 fire buttons
- SD card
- Two PS/2 connectors
- Power button
- Reset button
- Ear input
- I2S audio output
- Mini USB for main power supply
- AUX connector for extension, exposing free pins in both the Cyc1000 and the RP2040.

# Pinout
As of preview version 0.2 this is the pinout description

![Pinout](/doc/calypso-pinouts-0.2.png?raw=true "Calypso Pinouts")

# Support firmware
Firmware for the RP2040 MCU is so far a fork of zxmicrojack for RP2040 based Mist (https://github.com/ZXMicroJack/mist-firmware-rp2040) modified for calypso. The aim is to develop a specific and more minimalistic firmware since the current one was used mostly for board validation purposes. The forked firmware can be found here: https://github.com/teiram/mist-firmware-rp2040 

> [!NOTE]  
> I'm happy to share that we have now an oficial firmware for the board. It's still in a preliminary stage but should support most of the needed feature for Mist compatibility > and you can find it here: https://github.com/teiram/calypso-firmware/


# Disclaimer
This is a personal project I started with the support of the RetroWiki FPGA Dev community (thank you guys). There is no aim for commercial benefit neither I will provide any warranty or support beyond what my free time allows for. Feel free to build the board for your personal use, or a limited batch of units for your pals. It works for me, but I tested it with a very limited set of hardware, so your milleage may vary.
Enjoy ;)

# Errata, issues
## Version 0.3
- Fixed Q2 footprint and updated values for C16 and C17. This version is so far untested, but since Q2 issue was fixed manually without need ro reroute the board again, there are good chances it's safe to use.
  
## Version 0.2
- Q2 footprint is wrong. The schematic shows a BC547 but a SMD BC847 was intended. Unfortunately the pinout doesn´t match. So in case you want to use the composite video output you need to adjust it accordingly. A BC847 can be installed by rotating it 90º counterclockwise, what makes soldering a bit trickier but it can be done.
- The board supports RP2040 clones known as YD-2040 by VCC-GND studio. An official RP2040 won´t work completely due to:
  - The SWD header in the official RP2040 has 3 pins instead of 4 pins, so you cannot take advantage of the SWD/UART connector but you can still attach your SWD device directly to the RP2040.
  - YD-2040 exposes GPIO 23 on pin 37, which is not the case for in the official RP2040. Unfortunately GPIO23 is used for one of the DB9 joystick directions, and therefore a DB9 joystick won't work properly with an official RP2040
  - The YD-2040 doesn´t expose VBUS on the breakboard pins, therefore USB devices can only be used if they are self-powered or connected through a self-powered USB hub. The official RP2040 exposes VBUS and therefore it would be possible to power the bus without the need of a powered hub. But since the design was based on the YD-2040 there is no provision for that. This might be addressed in future releases.
