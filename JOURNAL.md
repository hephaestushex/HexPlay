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

# July 4th:

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

- 12mm Tactile Switch Buttons x7
- 12mm Tactile Switch Buttons Right Angle x4
- Analog Joystick x2
- MCP3008 - 8-Channel 10-Bit ADC With SPI Interface x1

### Audio

- Stereo 3.7W Class D Audio Amplifier MAX98306 x1
- Mono Enclosed Speaker with Plain Wires - 3W 4 Ohm x2

### Battery/Charging

- 18650 Li-ion Batteries x2
- Adafruit Powerboost 1000 Charger



