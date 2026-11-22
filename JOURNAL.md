---
Title: Radio Frequency Card Scanner
Author: locusdeveloper7
Description: A simple custom RF card scanner to check for access level.
Created On: 8/4/2026
---

# October 30th: Project Start!!

I began the project with the goal of creating a custom card scanner that could check if a student is present to class -- AKA an attendance system. The first thing I really had to think about was the type of microcontroller I was going to use, one that is strong enough to support WIFI, Memory, and Pin Configurations. So, the one that I landed with is the ESP32-S3. While I know that this microcontroller is overused in many projects, I think it is relatively simple to understand without having to introduce any complexity, and the manufacturers provide a generously comprehensive datasheet.

To think things through, I need to list what are of importance in this project. Specifically speaking, what goes into actually making these circuit boards work. I compiled a simple rundown of what needs to be added into the project to have a FUNCTIONAL microcontroller -- Just the microcontroller by the way! This does not include the other sensors and whatnot.

* ESP32-S3 Microcontroller
* USB-C Connector
* Voltage Regulator
* Crystal Oscillator (for precise timings)
* Electrostatic Discharge Protection (ESD)
* Boot and Reset Switches
* And external pins for debugging

The ESP32-S3-WROOM-1 <br>
<img width="447" height="447" alt="image" src="https://github.com/user-attachments/assets/e3c7764b-cce8-4977-8ade-b726e783c7c6" />

For the RFID module, I was thinking of using this model - the RC522.
<img width="600" height="510" alt="image" src="https://github.com/user-attachments/assets/dc5e95bf-3e14-4655-a9e5-f7938d9c53a2" />


I think that this is enough for the day. Tomorrow, I will begin working on the USB-C and Voltage Regulator! Two very important parts of the microcontroller.

**Total time spent: 10m**

# October 31st: USB-C and Voltage Regulator Created!

Small but important checkpoints! These two parts did not take long to create. 

## USB-C
The USB-C was straightforward, but I did include a small and easily unnoticed component in the schematic - a polyfuse. And you may be wondering...what in the world is that? A bomb? Basically, a polyfuse is this component that increases its resistance when the current gets VERY high or there is excess heat.

<img width="622" height="622" alt="image" src="https://github.com/user-attachments/assets/282db22d-3c93-47cd-af8e-5837552c53a3" />

## Voltage Regulator
For the voltage regulator, I went with the AP2112K-3.3 because it is considered the standard and recommended. But the other reason why it is used is because the ESP32-S3 can require 350-500mA using WIFI and Bluetooth, but this regulator provides a stable 600mA current, well above the required threshold. Also, the IC is compact and small enough to not take up too much space.

<img width="696" height="584" alt="image" src="https://github.com/user-attachments/assets/58b1e425-5458-497e-b2ae-52832cebde3a" /><br>

**Total time spent: 30m**

# November 15th: Added a Charging Circuit

Sooo...I am back. School got in the way. Yes lots of homework. But AP Calculus is not bad at all!

## Charging Controller
Anyways, picking up where I left off. I had remembered I finished working on the USB-C and Voltage Regulator, so I thought it would make logical sense to include some type of charging system in order to make the PCB standalone - this is for classroom attendance after all and wouldn't standalone be cooler? Plus, it would allow the instructor to put it anywhere in the classroom that seems appropriate. 

<img width="666" height="538" alt="image" src="https://github.com/user-attachments/assets/85763dda-d45d-48f0-8665-631bced02cb3" />

This part was recommended by Google because I didn't know what was recommended for the ESP32-S3 specifically. As I read the datasheet, I was intrigued. Apparently, it allows for both Lithium-ion and USB charging. So the idea of having two types of power sources was an immediate excitement boost! This component wasn't too bad to connect together as I just used their reference schematic. But...I did try and managed to understand how it works, just so I don't mess anything up.

**Total time spent: 30m**

# November 20th: Starting the RF layout...
This radio frequency stuff is starting to stress me out. First, I did not realize how difficult this truly would be. And second, there is soooo much math involved to the point where it's not funny. Also, I just learned that a small inaccurate value could mess up the whole thing.

Okay, so, I downloaded a premade MFRC522 symbol from SnapEda, and it made things a little easier because I have a component that is a little familiar since I was going to use KiCad's one and only PN5120A0HN1, but its documentation was a bit difficult to understand.

This is my current progress

<img width="647" height="728" alt="image" src="https://github.com/user-attachments/assets/7ad5c683-b41f-4361-8aaf-29d241ac53d8" />

Update later on in the session. This is the result with the help of Google Gemini.
Note: I manually put the parts together and did not have AI do it for me.

<img width="611" height="719" alt="image" src="https://github.com/user-attachments/assets/869c39dc-9a56-416f-a018-d4d91f4c0a7c" />

**Total time spent: 1h10min**

# November 21st: RF Update!!!! & Extra Additions

This is the BIGGEST breakthrough! Alright, I was using Gemini, and it recommended this website that could help me choose the specific values for the RF layout. All I need to do now is to come up with the dimensions for the PCB. Nothing to out of the ordinary, just something that is large enough to scan a card and also hold the important electronics on one side.

Quality Factor Equation
The desired Q value is to be 25 which is below the max value of 35.

<img width="175" height="123" alt="image" src="https://github.com/user-attachments/assets/ee571c8a-0471-4a6b-a7f0-2025c65c0e7c" />

