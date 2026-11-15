# Parts you solder yourself (through-hole)

JLC fits every part, through-hole connectors included (since 15 Nov). Only these optional
debug headers are left for you:

| Ref | Function | Part |
|---|---|---|
| J3 | JTAG | 6 pins from the 1x40 header (C2337), optional |
| J7 | ESP UART | 4 pins from the 1x40 header (C2337), optional |

J3 (JTAG) and J7 (ESP UART) are optional debug headers: the board is programmed over USB-C
(FT2232H JTAG + UART) and the ESP32 from Linux, so fit them only if you need them.
