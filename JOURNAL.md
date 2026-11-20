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

## Universal Serial Bus (USB)
Added the USB-C with a Polyfuse (a fuse that prevents over-current to the microcontroller)
<img width="622" height="622" alt="image" src="https://github.com/user-attachments/assets/282db22d-3c93-47cd-af8e-5837552c53a3" />

## Voltage Regulator
For the voltage regulator, I went with the AP2112K-3.3 because it is considered the standard and recommended. But the other reason why it is used is because the ESP32-S3 can require 350-500mA using WIFI and Bluetooth, but this regular provides a stable 600mA current, well above the required threshold. Also, the IC is compact and small enough to not take up too much space.

<img width="696" height="584" alt="image" src="https://github.com/user-attachments/assets/58b1e425-5458-497e-b2ae-52832cebde3a" /><br>
Datasheet: https://www.diodes.com/assets/Datasheets/AP2112.pdf

| Pin Name | Number | Function |
| :--------: | :--------: | -------- |
| VIN | 1 | Input Voltage, 5V - Unstable |
| GND | 2 | Ground |
| EN | 3 | Chip Enable, High - Normal Operation, Low - Shutdown |
| VOUT | 5 | Output Voltage, 3.3V - Stable |

## Result/Outlook
While I understand that a project like this could be designed using an Arduino and an external RFID reader and an LCD Display, this design serves a practical purpose that the Arduino cannot replicate. Since the Arduino does not have a dedicated WIFI system it would make sense for me to create a custom PCB that could handle cloud updates and also offline data logging for an attendance system. And if needed, the PCB could also be used either USB for power or battery to allow it to be mobile/standalone.

**Total time spent: 30m**

# October 31st: Adding a crystal oscillator and data-line protection

The next step in the project is to actually connect the ESP32-S3 to the other peripherals. The KiCad library already has a premade symbol for the ESP32-S3 module so that takes away the external time that could have been used to make the symbol.

## ESD Protection
This specific ESD Protection component is known for being highly reliable and maintains the USB data signal line with low capacitance.

<img width="669" height="645" alt="image" src="https://github.com/user-attachments/assets/0ca888e8-8e67-4533-b233-fa25d573d059" /><br>
Datasheet: https://www.st.com/resource/en/datasheet/usblc6-2.pdf

<br><br>

<img width="804" height="607" alt="image" src="https://github.com/user-attachments/assets/32af156f-6431-4f05-98a5-66e5428551f3" />

I added an optional crystal oscillator in order to allow the ESP32-S3 to achieve precise timings. The documentation recommended a frequency of 32.768KHz.
<br>
**Total time spent: 45m**

# November 14th: Progress Update

So, I have been taking a bit of a break from the project. 

**Total time spent: 5m**

# November 15th: Charging IC | RF Filter Section
<img width="827" height="678" alt="image" src="https://github.com/user-attachments/assets/84cf92dc-ca41-4430-b9a7-0da5c2c23899" />
<img width="803" height="710" alt="image" src="https://github.com/user-attachments/assets/012cfc3f-c093-4e3f-b336-b080e2d94a80" />

Datasheet: https://ww1.microchip.com/downloads/en/DeviceDoc/20001984g.pdf
https://community.nxp.com/pwmxy87654/attachments/pwmxy87654/wireless-connectivity/12935/3/AN1445.pdf

|---|---|

**Total time spent: 5m**

# November 20th: Locked in and got the RFID 

