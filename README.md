# Digital Picture Frame

Open source picture frame featuring a colored e-Ink display and impressive low power consumption

## Description

The goal is simple - using the latest technologies of colored e-Ink displays, create a digital picture frame with the capabilities of periodic refreshes to the displayed picture.
This project focuses not only on functionality, but also on power efficiency, in order to obtain the longest battery life with small footprint batteries.

## Architecture

The architecture is simple. There are three main components on the system - the microcontroller, the display and the micro SD card.
The microcontroller features an internal RTC that periodically dispatches the **Refresh** Procedure. Here are it's steps:

* Power up and initialize the communication with the micro SD card.
* Power up and initialize the communication with the e-Ink display.
* Fetch a random image from the FAT32 file system of the card.
* Stream the raw image data to the display.
* Wait until the display finishes refreshing.
* Power down the micro SD and e-Ink display.
* Enter _deep sleep_ mode.

## Material

At the moment, the targeted display is the 7.3' 7-Color display, from Waveshare ([link](https://www.waveshare.com/product/7.3inch-e-paper-f.htm)).

A good compromise between power efficiency, price, availability and footprint make the STM32L0 family a suitable microcontroller.
At the moment, the targeted microcontroller is the STM32L010K8.
It also has an internal RTC, simplifying the design.
