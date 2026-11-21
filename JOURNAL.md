---
Title: Radio Frequency Card Scanner
Author: locusdeveloper7
Description: A simple custom RF card scanner to check for access level.
Created On: 8/4/2026
---

# October 30th: Project Start!!

I began the the project with the goal of creating a custom card scanner that could check if a student is present to class -- AKA an attendance system. The first thing I really had to think about was the type of microcontroller I was going to use, one that is strong enough to support WIFI, Memory, and Pin Configurations. So, the one that I landed with is the ESP32-S3. While I know that this microcontroller is overused in many projects, I think it is relatively simple to understand without having to introduce any complexity, and the manufacturers provide a generously comprehensive datasheet.

To think things through, I need to list what are of importance in this project. Specifically speaking, what goes into actually making these circuit boards work. I compiled a simple rundown of what needs to be added into the project to have a FUNCTIONAL microcontroller -- Just the microcontroller by the way! This does not include the other sensors and whatnot.

* ESP32-S3 Microcontroller
* USB-C Connector
* Voltage Regulator
* Crystal Oscillator (for precise timings)
* Electrostatic Discharge Protection (ESD)
* Boot and Reset Switches
* And external pins for debugging

I think that this is enough for the day. Tomorrow, I will begin working on the USB-C and Voltage Regulator! Two very important parts of the microcontroller.

**Total time spent: 10m**

# October 31st: USB-C and Voltage Regulator Created!

Small but important checkpoints! These two parts did not take long to create. 

## USB-C
The USB-C was straightforward, but I did include a small and easily unnoticed component in the schematic - a polyfuse. And you may be wondering...what in the world is that? A bomb? Basically, a polyfuse is this component that increases its resistance when the current gets VERY high or there is excess heat.

<img width="622" height="622" alt="image" src="https://github.com/user-attachments/assets/282db22d-3c93-47cd-af8e-5837552c53a3" />

## Voltage Regulator
For the voltage regulator, I went with the AP2112K-3.3 because it is considered the standard and recommended. But the other reason why it is used is because the ESP32-S3 can require 350-500mA using WIFI and Bluetooth, but this regular provides a stable 600mA current, well above the required threshold. Also, the IC is compact and small enough to not take up too much space.

<img width="696" height="584" alt="image" src="https://github.com/user-attachments/assets/58b1e425-5458-497e-b2ae-52832cebde3a" /><br>

**Total time spent: 20m**

# November 15th: Added a Charging Circuit

Sooo...I am back. School got in the way. Yes lots of homework. But AP Calculus is not bad at all!

## Charging Controller
Anyways, picking up where I left off. I had remembered I finished working on the USB-C and Voltage Regulator, so I thought it would make logical sense to include some type of charging system in order to make the PCB standalone - this is for classroom attendance after all and wouldn't standalone be cooler? Plus, it would allow the instructor to put it anywhere in the classroom that seems appropriate. 

<img width="666" height="538" alt="image" src="https://github.com/user-attachments/assets/85763dda-d45d-48f0-8665-631bced02cb3" />

This part was recommended by Google because I didn't know what was recommended for the ESP32-S3 specifically. As I read the datasheet, I was intrigued. Apparently, it allows for both Lithium-ion and USB charging. So the idea of having two types of power sources was an immediate excitement boost! This component wasn't too bad to connect together as I just used their reference schematic. But...I did try and managed to understand how it works, just so I don't mess anything up.

**Total time spent: 30m**

# November 20th: Locked in and got the RF Filter Laid Out!!!!

Before going into the exciting progress made today, I have to be completely honest...I had to go back through the older entries to remove the overly "formal" tone -- they sounded more like a Read Me file than an actual journal.

