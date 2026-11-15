# Parts you solder yourself (through-hole)

JLC places every SMD part. These are cheaper and sturdier hand-soldered:

| Ref | Function | Part |
|---|---|---|
| BZ1 | 3V active | TMB12A03 3 V active buzzer, 7.6 mm pitch (C96222) |
| J1 | 12V DC in | XKB DC-005-5A-2.0 barrel jack, 5.5/2.1 mm (C381116) |
| J3 | JTAG | 6 pins from the 1x40 header (C2337), optional |
| J7 | ESP UART | 4 pins from the 1x40 header (C2337), optional |
| J8 | E-STOP (NC) | KF128-5.08-2P screw terminal (C474952) |
| J9 | TAMPER (NC, jumper if unused) | 2 pins from the 1x40 header (C2337) + jumper cap |
| J10 | ARM KEY | KF128-5.08-2P screw terminal (C474952) |
| J11 | OLED | 1x4 2.54 mm female header (C2718488) |
| J12 | FAN | JST B3B-PH-K-S (C131339) |
| J13 | PMOD JA | CJT A2541WR-2x6P right-angle 2x6 female, 2.54 mm (C239337) |
| JP1 | BOOT MIO5 | 3 pins from the 1x40 header (C2337) + jumper cap |
| JP2 | BOOT MIO4 | 3 pins from the 1x40 header (C2337) + jumper cap |
| JP3 | WDT OFF | 2 pins from the 1x40 header (C2337); jumper only for bench work |
| JP4 | BYPASS | 2 pins cut from a 1x40 2.54 mm header (C2337) + jumper cap |

J3 (JTAG) and J7 (ESP UART) are optional debug headers: the board is programmed over USB-C
(FT2232H JTAG + UART) and the ESP32 from Linux, so fit them only if you need them.
