# HexPlay
A handheld gaming console powered by the Raspberry Pi 4/5. This handheld will run Android, using the touchscreen provided by the display. With 2 analog sticks and 15 more inputs, this will be able to play any game upto GameCube (using pi 5) or N64 (using pi 4). The handheld uses a powerbank to provide power to the handheld. This handheld is somewhat cold-swappable, with all connections to the pi is hdmi or usb.

I made this project for several reasons. Number one: points for flight reimbursement. Number two: my pi 4 was laying around, collecting dust. Number three: I've always loved playing retro games, especially those of the GameCube. I couldve made a simple handheld, with no analog joystick, but I found that unappealing because I wanted to play games with analog sticks. The HexPlay was born from there, going through many iterations, from a pcb handheld, an xbox style handheld, to the nintendo switch esque handheld that is here today. Overall, this project was a dream of mine ever since I got my pi, and its so nice to see it come into fruition 5 years later.

<img width="1046" height="516" alt="image" src="https://github.com/user-attachments/assets/39243b10-da81-4d47-90a5-c4992b29227d" />

<img width="1148" height="389" alt="image" src="https://github.com/user-attachments/assets/a07edf94-3072-410e-9cee-1220ddcb09c7" />

<img width="939" height="665" alt="image" src="https://github.com/user-attachments/assets/6a7de390-b4be-4add-880c-c83174cab823" />

Uses GP2040-CE firmware - [link](https://gp2040-ce.info/)

# CAD

I have some M3x6 bolts and M3x5x4 heatset inserts left over from my keyboard, so I designed my case around them.

The joysticks are clamped in place with 4 posts, each with slots for m3 inserts.

<img width="455" height="372" alt="image" src="https://github.com/user-attachments/assets/fcb6ea45-5067-406e-a625-6e01e2199403" />

The buttons will simply be inserted and hot glued.


# Schematic

<img width="1076" height="612" alt="image" src="https://github.com/user-attachments/assets/11029510-1477-4594-8696-b4c29b25fc47" />

The schematic is just a wiring diagram, I am not using a PCB due to the components used. The display takes up most of the space, and the Pi is mounted behind it. Since I always intended to use an mcu as a bridge between the pi and the controls, there wasn't really a point to a pcb, as it would just complicate things (add one more thing to deal with in cad). Additionally, the joysticks would stick too far up from the controls if i were to mount it all on one flat plane. Another reason for not using a PCB is for the shoulder buttons. If I were to use shoulder buttons, I would need right angle buttons, which would increase the cost and complexity.

<img width="642" height="634" alt="image" src="https://github.com/user-attachments/assets/c4af6015-e603-4a80-ae16-2fb0974e4455" />

The connections from the Pi are pretty simple. The power bank plugs into the power socket, the mcu connects to a usb port, and the display connects to the pi via usb and microHDMI. Most connections are hidden behind a case, except for the powerbank connection. This is because I would like it to be cold-swappable, meaning I can just pop in a new power bank if the battery gets low.

<img width="687" height="394" alt="image" src="https://github.com/user-attachments/assets/861a6208-8a92-44ff-866f-12779b7627bf" />

The buttons are all individually wired. I didn't go with a matrix since it would add complexity (matrix, which would need a pcb, which I can't use because of components. Anyway, the RP2040 has more than enough GPIOs.

<img width="520" height="659" alt="image" src="https://github.com/user-attachments/assets/f380fa2c-8e6c-4444-a48a-517efae0e2e4" />

Here's an interesting part. The official Raspberry Pi Pico only exposes 3 ADC pins. The other ADC is tied to VSYS for power input sensing. The joysticks need 2 ADC pins each. Unfortunately, this means that I can't use a normal Pi Pico (or an orpheus pico for that matter) Luckily, other board expose all 4 ADC pins. One is the XIAO RP2040 and the other is the RP2040-Zero. The former doesnt have much pins (11 usable GPIOs) but the latter has more than enough. Anyway, the buttons are wired to some GPIOs.

# Software/Firmware

The RP2040-Zero runs GP2040-CE, a firmware that turns any RP2040 into a game controller. The firmware reads inputs from set pins, and outputs a signal to the pi with a less than 1ms latency. This is better than any custom firmware that I can make, plus, this firmware has been tried and tested by many people. As for the Pi, it will either run RetroPie or Android. Due to the nature of the controls and display, no other software needs to be written, as everything is plug and play. (Except for the display. The display will need some configuration options to work properly with the raspberry pi. But since this isn't firmware, im not counting it)

# BOM Notes

The two parts ordered off of Amazon are of same or less price than of aliexpress. Additionally, the power bank is from a reputable brand, so I don't burn my house down playing Zelda.

# BOM
| Name                              | Quantity  | Part Link                                                                                                                        | Description                                                | Price (USD) |
|-----------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|-------------|
| Raspberry Pi 4/5                  | 1         | already owned                                                                                                                     | brains of the handheld                                     | $55.00      |
| RP2040-Zero                       | 1         | [AliExpress](https://www.aliexpress.com/item/1005007650325892.html)                                                              | MCU for handling joystick and button input                | $5.15       |
| Analog PS2 style Joystick         | 2         | [AliExpress](https://www.aliexpress.com/item/1005007561985496.html)                                                              | Analog joystick for input                                 | $1.69       |
| Soft Tactile Buttons              | 15        | [AliExpress](https://www.aliexpress.com/item/32963848918.html)                                                                   | button for input source                                   | $1.81       |
| 7" Touchscreen Display with Speakers | 1      | [Amazon](https://www.amazon.ca/ELECROW-Raspberry-Touchscreen-1024x600-HDMI-Compatible/dp/B08FMNDDSL/)                            | touchscreen display with speakers                         | $47.49      |
| Equivalent AliExpress Display     | 0         | [AliExpress](https://www.aliexpress.com/item/1005001315929149.html)                                                              | touchscreen display with speakers                          | $61.50     |
| 3D Printed Case and Buttons       | 1         | already owned                                                                                                                     | custom case and buttons for the handheld                  | $4.00       |
| Wires                             | a lot     | already owned                                                                                                                     | for connecting components                                 | $1.00       |
| 10000mAh Power Bank               | 1         | [Amazon](https://www.amazon.ca/INIU-Portable-Slimmest-10000mAh-Charging/dp/B0DCHVGS2S/)                                          | Power bank for powering the device                        | $23.38      |
| Equivalent AliExpress Power Bank  | 0         | [AliExpress](https://www.aliexpress.com/item/1005008324698030.html)                                                               | powerbank. amazon also ships faster than ali for less    | $36.67      |
| M3x6 Bolts                        | 14        | already owned                                                                                                                     | for securing components                                   | $0.50       |
| M3x5x4 Heatset Inserts            | 14        | already owned                                                                                                                     | for securing components                                   | $0.50       |
|  |  |  | Total | $152.60 |
|  |  |  | Hack Club Total | $79.52 |
