# Ordering the OFE trader board at JLCPCB (rev A)

Upload `ofe_trader_revA_JLCPCB_Gerbers.zip` at jlcpcb.com → Order now. Then check every setting
below against what JLC shows. **You place the order yourself**; nothing here has been submitted.

**Release checks (14 Nov 2026, `design/finish.py`):** KiCad DRC 0 errors and 0 unconnected on 6
layers, schematic parity 0, DDR3L timing check PASS (`kicad/ddr_report.md`: worst address/command
+94 ps vs CK, worst DQ +32 ps vs DQS, limit +-100 ps). Remaining DRC warnings are cosmetic: 44
silkscreen-near-edge (JLC trims silk at the edge) and 1 copper sliver.

## PCB settings
| Setting | Value | Why |
|---|---|---|
| Base material | FR-4 | |
| Layers | **6** | detected from the zip |
| Dimensions | **130 × 100 mm** | detected from the zip |
| PCB qty | 5 | JLC minimum |
| Product type | Industrial/consumer | |
| PCB thickness | **1.6 mm** | |
| Impedance control | **Yes, JLC06161H-1080** | the stackup the DDR widths were sized for |
| Via covering | **Epoxy filled & capped** (POFV) | via-in-pad under the Zynq and RAM. Free on 6+ layers |
| Min via hole / diameter | **0.2 mm / 0.4 mm** | via-in-pad under the Zynq |
| Surface finish | **ENIG** | flat pads for the 0.8 mm and 0.5 mm BGAs (HASL isn't flat enough) |
| Outer copper | 1 oz | |
| Inner copper | 0.5 oz | |
| Solder mask | Green (any colour works; green is fastest) | |
| Silkscreen | White | |
| Remove order number | Specify a location, or pay to remove (optional) | |
| Gold fingers, castellated holes, edge plating | No | |

## Assembly (PCBA)
| Setting | Value |
|---|---|
| PCBA type | **Standard** (BGAs need Standard, not Economic) |
| Assembly side | **Top side** (all SMD parts are on top) |
| PCBA qty | **2** (assemble 2 of the 5; keep 3 bare for a second attempt) |
| Tooling holes | Added by JLC |
| Confirm parts placement | **Yes** (JLC's engineer checks rotation/polarity before the build) |
| Depanel / X-ray | Ask for **X-ray inspection** of the BGAs if it's offered |

Files: BOM = `ofe_trader_BOM_JLCPCB.csv`, CPL = `ofe_trader_CPL_JLCPCB.csv`.

On the BOM page:
1. Every line should match an LCSC part. If a part shows as out of stock, tell me which one and
   I'll swap it in `design/bom_db.py`. Don't pick a substitute by hand.
2. Check JLC's 3D placement preview carefully:
   - the dot / pin-1 corner of every IC (Zynq U1, RAM U2, FT2232H U4, the regulators);
   - the stripe of diodes D1–D3;
   - the + side of the 470 µF capacitor C2;
   - the LED polarity.

   If one is rotated, fix it there or tell me.
3. The **Zynq (C2988113)** is an Extended part with low stock. If it needs "pre-order", that
   adds days.

## Parts you solder yourself
See `HAND_SOLDER.md` for the list (barrel jack, screw terminals, headers, buzzer, OLED socket,
fan connector, PMOD socket and the like). Order them from LCSC in the same cart.

## Expected cost (rough, 12 Nov 2026)
For 5 boards with 2 assembled, before shipping, about US$450–550:
- **Bare board:** about US$60–90 (6-layer, impedance control, ENIG).
- **Zynq XC7Z020:** 2 × ~US$93.
- **RAM:** 2 × ~US$16.
- **Everything else:** ~US$25 per board.
- **Setup fees:** about US$3 for each Extended part. JLC shows the exact count, and several parts
  are Basic, which have no fee.

There is no eMMC, QSPI flash, Ethernet or RTC on rev A (see PLAN.md "Rev A trims"). The board boots and
runs Linux from a microSD card and goes online over the ESP32's Wi-Fi; use a
high-endurance one (e.g. SanDisk High Endurance 32 GB).
JLC's quote is the real number.

## Expansion port
J13 is a standard PMOD host port, so the spare board can be reused for other projects
(ADC, motor driver, display, GPS and Ethernet modules all plug in). Solder the right-angle socket
yourself (`HAND_SOLDER.md`).
