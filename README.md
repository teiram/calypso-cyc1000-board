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
