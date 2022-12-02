# Adafruit_SH1106: Library compatible with Adafruit for SH1106

## General information:

This is a SH1106 chip driver library that is compatible with the Adafruit_SSD1306 library for oleds/lcds but can compile and work  with Arduino framework for STM32 based boards (Tested on platformio).

Several Oled screens use the SH1106 chip instead of the more common ssd1306 chip which means we need to use this library to drive them. 

This version is based on the original version located at: [Adafruit SH1106](https://github.com/wonho-maker/Adafruit_SH1106) that works for standard arduinos and ESP32 but does not compile with the Arduino framework for the STM32s. So there are some code changes to make it to compile for the STM32 Arduino framworks. If not using STM32s use the original library.

This SH1106 driver similar to SSD1306 and compatible with other Adafruit libraries with the only necessary modifications on the initialization process for the **display()** function:

```
#include <Adafruit_SH1106.h>

#define OLED_RESET 4
Adafruit_SH1106 display(OLED_RESET);

void setup()   {
  Serial.begin(9600);

  // by default, we'll generate the high voltage from the 3.3v line internally! (neat!)
  display.begin(SH1106_SWITCHCAPVCC, 0x3C);  // initialize with the I2C addr 0x3D (for the 128x64)
  // init done

  // Show image buffer on the display hardware.
  // Since the buffer is intialized with an Adafruit splashscreen
  // internally, this will display the splashscreen.
  display.display();

  // From this point business as usual....

```
 
## Instalation:

 Just download and unpack it under the **lib** folder on yor Platformio based project. You should end with **<project>/lib/Adafruit_SH1106/**

## Testing:

 Just load one of the examples from the **examples** folder, changing the OLed connecting pins as necessary.

 I've tested on a I2C SH1106 1.3' OLED from Diymore connected to a STM32F411CE WeAct BlackPill board with success.
