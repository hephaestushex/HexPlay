---
title: "HexPlay"
author: "hephaestushex"
description: "A handheld gaming console powered by the pi 4"
created_at: "2024-06-24"
---

# June 24th: Initial Planning

I initially wanted to make a retro gaming handheld with the pi zero 2w. I didn't like the idea of only being able to play retro games, so I decided to modify it to play any game. Since the pi zero 2w is underpowered, it would have to be replaced with a more powerful sbc. A pi 5 would be ideal, but since it would eat at my budget, I'm going to use a pi 4 4gb that I already own. This console should be able to play retro games, plus a few more, like minecraft. In this case, it is essential that the pi 4 is overclocked, but in order to not damage the pi, it would have to be cooled. Additionally, it would make sense for the display to be touchscreen, as a gaming controller wouldn't be an effective method of navigation.

With that initial brainstorm, a list of capabilities and things to do can be made.

Capabilities

- Play retro games
- Play modern games
- Touchscreen
- Easy to use controls
- Effective cooling

From there it would make sense to research components to use.

I liked [this](https://www.amazon.com/ELECROW-Raspberry-Monitor-Touchscreen-Capacitive/dp/B0CYKXCM8J?th=1) display used in a console designed by Leandro Linares over [here](https://leandrolinares.com/blog/diy-handheld-game-console/).

This display is only $38 USD, plus it handles audio/video plus touchscreen in one package.

As for controls, I want this to have a DPAD, A/B/X/Y buttons, L1/L2/R1/R2 Shoulder Buttons, 2x Analog Joysticks, start/select, and a hotkey button. More buttons may be added, but these were my bare minimums. Since the Pi does not have an ADC, I would need to use an external chip. In my use case, an external chip would be better.

For power management, I would like to have used the pisugar. Unfortunately, this would be too expensive, so I would have to use a lipo with a charging board.

I then took some time to create a few sketches to see what it would look like.

![sketch](https://github.com/user-attachments/assets/7f7d99ce-7f09-46d1-a8ea-91be1433fe84)

![sketch_0001](https://github.com/user-attachments/assets/e9e791d8-a668-49f7-9347-e6e6b660cc71)

With this out of the way, it was time to check out cooling. From my search, it seems like over clocking then cooling the pi is simply not worth it, so certain games will not be able to run, which is given, since this is a pi 4. I will simply stick to the heatsinks that came with my Pi.

Thats all the planning I did today

**Total time spent: 30mins**

# July 4th: tentative planning

11:23

I noticed that the repo didn't have hexplay on it, so I renamed it.

I don't think there is much to do, so I just decided to jump in by creating a schematic.

But firstly, I wanted to create a list of all the electronic components, grouped by function

## Electronic Components:

### Computer

- Raspberry Pi 4B x1

### Display

- ELECROW 5" Mini Touchscreen Display x1

### Controls

- 12mm Tactile Switch Buttons x11
- 12mm Tactile Switch Buttons Right Angle x4
- Analog Joystick x2
- MCP3008 - 8-Channel 10-Bit ADC With SPI Interface x1

### Audio

- Stereo 3.7W Class D Audio Amplifier MAX98306 x1
- Mono Enclosed Speaker with Plain Wires - 3W 4 Ohm x2

### Battery/Charging

- 18650 Li-ion Batteries x2
- Adafruit Powerboost 1000 Charger

**Total time spent: 1.5 hours**

# July 29th: Start actual design

I procrastinated alot, so I actually started today after a while. I didn't actually like the setup above, so I want to change it a little. After a good 1 and a half hours to talking to ChatGPT and some research on GP2040-CE, here's my setup. What influenced this is the fact that Jumpstart exists, and building a similar level of emulation is pointless. I want this to be better. Here's the final setup, all using HDMI cables and USB Cables. Also, this setup will be able to switch computers easily, as in, I'll use my pi 4 to run it, and after getting a pi 5, use that instead. The setup will also be powered by a powerbank, as the 18650 cells I have do not deliver enough power 5V/5A - 25W. My two batteries combined have 14.8 Wh. That's even less than one hour runtime on the Pi 4 (15W). I could get a lipo, but that still causes the issue of charging and discharging. Most of the solutions nowadays aren't great. So, heres the final setup.

### Display and Audio

I upgraded to the 7 inch version of the display for two reasons. 
A: the display is bigger, making 3d games a lot more playable
B: Built in speakers make this project a whole lot more simpler.

[link to display](https://www.amazon.com/ELECROW-Raspberry-Touchscreen-Capacitive-1024x600/dp/B08FMNDDSL/ref=sr_1_3?crid=2WME5A6UNDQ7L&dib=eyJ2IjoiMSJ9.Wm0-hnTPbDDn0vqaFVCSlXVC4DqmXFiNDiHnSNQvLFh5KOTJWLzAUIheSNe0HNXcG2e27HJYZj7qNdNidxRvVRCRMixbhqDQn_SwQT8J_-WzUr_rk_lSaDCt5wKiA1Ro_aTsGIr7o0GGEvoPDXDe8Ea4XvEOEs9wwfxaZvUPeIGxLKMJGUybYM8BofdgqFvkI9u-UglnfW3_LAsjVLKlVkfDqZuJ9RJVrGHIA2v8P0w.mMPB3jiySEeW34D-E4EGS3c3dAbJJl1rEAIFKYb64Ns&dib_tag=se&keywords=ELECROW%2B7%2BInch%2BTouchscreen%2BMonitor%2Bfor%2BRaspberry%2BPi%2B-%2B1024x600%2BIPS%2BCapacitive%2BTouch%2BScreen%2BHD%2BMini%2BLCD%2BDisplay%2Bwith%2BStand%2BCompatible%2Bwith%2BRaspberry%2BPi%2B5%2F4B%2F3B%2B%2F3B%2C%2BBB%2BBlack%2C%2BWin11%2F10%2F8%2F7%2C%2BDriver%2BFree&qid=1753934649&sprefix=elecrow%2B7%2Binch%2Btouchscreen%2Bmonitor%2Bfor%2Braspberry%2Bpi%2B-%2B1024x600%2Bips%2Bcapacitive%2Btouch%2Bscreen%2Bhd%2Bmini%2Blcd%2Bdisplay%2Bwith%2Bstand%2Bcompatible%2Bwith%2Braspberry%2Bpi%2B5%2F4b%2F3b%2B%2F3b%2C%2Bbb%2Bblack%2C%2Bwin11%2F10%2F8%2F7%2C%2Bdriver%2Bfree%2Caps%2C144&sr=8-3&th=1)

After looking around, this display seems pretty good.

### Computer

I plan on using my pi 4, and upgrading to the pi 5 which I plan to get from Summer of Making. As for cooling, the active cooler is pretty cheap at $7 CAD, which I can pay out of pocket later. 

### Controls

As for the controls, the seeed xiao rp2040 has 4 analog pins. I can put the buttons in a matrix for the other buttons.

The xiao has 11 usable GPIOs, with 4 being taken for analog input. That leaves us with a 7 remaining pins. that leaves us with 12 buttons. I need 17. 

That won't work. I have an adc, plus a orpheus pico. I could connect the adc for analog input use the other pins for switches. Phew. that will work.

As for the joysticks, I'll buy some joysticks you'd find in an arduino kit.

### Power

This is simple. Buy a power bank and use that to power the pi. 

### Case

This will be 3d printed

### Mounting

As I'm very close to the deadline, a pcb is unfeasible. This is ok anyway, as a PCB is hard, since that would constrain elements to a set height, plus the joysticks that are the most simple wouldn't mount to a pcb anyway.

What i'll most likely do is design holes on the case for some simply tactile pushbuttons to mount to, and I'll hot glue in the buttons, and solder wires from the legs to the pico. This setup is simple, and is way cheaper than making a pcb.

That's all i did today.

**Total time spent: 3h**

# July 30th: Schematic Speedrun

Time for a speedrun!

With the specs set above, this is what I got in terms of controls

<img width="898" height="720" alt="image" src="https://github.com/user-attachments/assets/75de1064-051d-4a34-8871-c64672e2260e" />

Looks like after looking at what Highway wants, i need to create a diagram for all the wiring. After messing around in other editors, I just created some custom symbols in KiCAD and ended up with this as my image.

<img width="628" height="628" alt="image" src="https://github.com/user-attachments/assets/79525e09-7762-41ba-b42f-414dc5e15ad1" />

After this, its just CAD and some code for the pi.

It's pretty late for me so thats it for today

**Total time spent: 1h**

# July 31st: Everything Speedrun

After procrastinating some more, I started filling out the BOM.

<img width="714" height="152" alt="image" src="https://github.com/user-attachments/assets/f5f94d90-da17-40d1-8d79-67bb9855b78d" />

All was fine until the powerbank. I spent so long on this for two simple reasons. The Pi 5 needs 5V/5A to run accessories. most powerbanks only have 5v/3a. I spent so long looking for a solution, with lipos, liions, tp4056 modules, buck/boost converters. In the end i found a power bank that offered 5V/3A over two ports to power the display if needed. A bonus of this powerbank is that it already has a usb-c cable built in, making the amount of cables one less.

Also while doing this, I realized that the ADC I have has pins soldered to it, plus I wanted to find a jank free setup. The Waveshare RP2040 zero solves this, but the only problem is that I would have to order this off of ali, which might delay the build process. As of writing this, I realized I can remove the headers. But, the adc is 8 bit (0-255) compared to the pico's 12 bit (1-4095). Anyway, I'll buy three things off of ali, the rp2040 zero, the joysticks, and some squishy buttons. The only issue with using the rp4040 zero is that I have to connect one button to a pad on the back, but thats better than using another chip with less accuracy. From here, I just have to make a table version of the bom, and cad up a design. In the last entry i mentioned making a custom firmware, but I found out about gp2040-ce, which makes controller firmware not only easy, but buttery smooth with a less than 1 ms latency.

With all that done, i hopped on fusion to design a case.

First step was to get the dimensions and get modelling. One interesting thing I did was use snipping tool to take a picture of the display to find the dimensions of the display, based off of a hdmi connector. As for mounting the display and joystick, i just inseted four corners and made a hole. After all of that, this is what I got

<img width="753" height="371" alt="image" src="https://github.com/user-attachments/assets/207fd223-2a7c-4db7-9e6b-01996a6e1549" />

its 5 mins to the deadline, so let me submit.


