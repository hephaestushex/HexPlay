# HexPlay
A handheld gaming console powered by the Raspberry Pi 4/5. This handheld will run Android, using the touchscreen provided by the display. With 2 analog sticks and 15 more inputs, this will be able to play any game upto GameCube (using pi 5) or N64 (using pi 4). The handheld uses a powerbank to provide power to the handheld. This handheld is somewhat cold-swappable, with all connections to the pi is hdmi or usb.

<img width="992" height="524" alt="image" src="https://github.com/user-attachments/assets/2a5ffcdc-e2e8-4c6c-ab6f-d9f003e2b731" />

<img width="1087" height="525" alt="image" src="https://github.com/user-attachments/assets/095fbeb2-ba7a-49b6-9a12-34c9353a3153" />

<img width="771" height="543" alt="image" src="https://github.com/user-attachments/assets/35a5168b-9df0-4477-9efa-2266cdb5c496" />

Uses GP2040-CE firmware - [link](https://gp2040-ce.info/)

# Schematic

<img width="1076" height="612" alt="image" src="https://github.com/user-attachments/assets/11029510-1477-4594-8696-b4c29b25fc47" />

The schematic is just a wiring diagram, I am not using a PCB due to the components used.

# BOM Notes

The two parts ordered off of Amazon are of same or less price than of aliexpress. Additionally, the power bank is from a reputable brand, so I don't burn my house down playing Zelda.

# BOM
| Name                              | Quantity  | Part Link                                                                                                                        | Description                                                | Price (USD) |
|-----------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|-------------|
| Raspberry Pi 4/5                  | 1         | already owned                                                                                                                     | brains of the handheld                                     | $55.00      |
| RP2040-Zero                       | 1         | [AliExpress](https://www.aliexpress.com/item/1005007650325892.html)                                                              | MCU for handling joystick and button input                | $5.15       |
| Analog PS2 style Joystick         | 2         | [AliExpress](https://www.aliexpress.com/item/1005007561985496.html)                                                              | Analog joystick for input                                 | $1.69       |
| Soft Tactile Buttons              | 15        | [AliExpress](https://www.aliexpress.com/item/32963848918.html)                                                                   | button for input source                                   | $1.81       |
| 7" Touchscreen Display with Speakers | 1      | [Amazon](https://www.amazon.ca/ELECROW-Raspberry-Touchscreen-1024x600-HDMI-Compatible/dp/B08FMNDDSL/)                            | touchscreen display with speakers                         | $59.57      |
| 3D Printed Case and Buttons       | 1         | already owned                                                                                                                     | custom case and buttons for the handheld                  | $4.00       |
| Wires                             | a lot     | already owned                                                                                                                     | for connecting components                                 | $1.00       |
| 10000mAh Power Bank               | 1         | [Amazon](https://www.amazon.ca/INIU-Portable-Slimmest-10000mAh-Charging/dp/B0DCHVGS2S/)                                          | Power bank for powering the device                        | $23.38      |
| M3x6 Bolts                        | 14        | already owned                                                                                                                     | for securing components                                   | $0.50       |
| M3x5x4 Heatset Inserts            | 14        | already owned                                                                                                                     | for securing components                                   | $0.50       |

