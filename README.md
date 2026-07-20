# IR Sensor PCB

A KiCad hardware project for a simple IR (infrared) sensor module, featuring an onboard comparator circuit, sensitivity adjustment, and status indication.

## Overview

This board implements a classic IR obstacle/proximity sensor design: an IR emitter/receiver pair feeds into a comparator IC, with a potentiometer to tune detection sensitivity and an LED to indicate detection state. Designed in KiCad.

## Bill of Materials

 Designator | Description        | Footprint                                    | Qty |

 D1, D2     | LED                | LED_D3.0mm_Horizontal_O1.27mm_Z2.0mm_Clear   | 2   |
 D3         | LED (status)       | LED_1206_3216Metric                          | 1   |
 J1         | 3-pin header       | PinHeader_1x03_P2.54mm_Horizontal            | 1   |
 R1, R2     | Resistor, 10k      | R_1206_3216Metric                            | 2   |
 R3         | Resistor, 10k      | R_1210_3225Metric                            | 1   |
 RV1        | Potentiometer, 10k | Bourns 3296W (vertical trimmer)              | 1   |
 U1         | 8-pin IC (comparator, e.g. LM358/LM393) | DIP-8 (0.3", 7.62mm)    | 1   |

> Note: U1's exact part isn't labeled in the netlist — most 3-pin IR sensor modules of this type use a dual op-amp/comparator (LM358 or LM393) in a DIP-8 package. Confirm against your schematic before ordering.

## Board Details

- **Layers:** 2-layer (F.Cu / B.Cu)
- **Board thickness:** 0.063 in (~1.6 mm, standard)
- **Front copper area:** 0.429 in²
- **Back copper area:** 0.077 in²
- **Min track width / clearance:** 0.0079 in (~0.2 mm)
- **Min drill diameter:** 0.0118 in (~0.3 mm)
- **Components:** 9 total (5 THT, 4 SMD), all on the front side
- **Pads:** 18 through-hole, 8 SMD
- **Vias:** 4 through-vias

## Connector (J1)

A 3-pin header, typically wired as:

| Pin | Function |
|-----|----------|
| 1   | VCC      |
| 2   | GND      |
| 3   | OUT (digital detection signal) |

> Confirm actual pinout against the schematic (`IR_SENSOR.kicad_sch`) before wiring.

## Repository Contents

 File                      Description                                  
 `IR_SENSOR.kicad_pro`    | KiCad project file                           
 `IR_SENSOR.kicad_sch`    | Schematic                                     
 `IR_SENSOR.kicad_pcb`    | PCB layout                                    
 `IR_SENSOR.kicad_prl`    | Local project settings (layer visibility etc.)
 `IR_SENSOR.csv`          | Bill of materials (BOM)                       
 `IR_SENSOR.rpt`          | KiCad DRC/electrical rules report             
 `IR_SENSOR_report.txt`   | PCB statistics report (board area, pads, vias)

## Getting Started

1. Install [KiCad](https://www.kicad.org/) (version 7 or later recommended).
2. Clone this repository:
   ```bash
   git clone https://github.com/riteshh27/IR-SENSOR-PCB.git
   ```
3. Open `IR_SENSOR.kicad_pro` in KiCad to view/edit the schematic and PCB layout.

## Manufacturing

To generate Gerber files for fabrication:
1. Open the PCB layout in KiCad.
2. Go to **File → Fabrication Outputs → Gerbers**.
3. Export the drill file alongside the Gerbers.
4. Zip the output folder and upload to your preferred PCB fab (JLCPCB, PCBWay, etc.).

## License

See [LICENSE](LICENSE) for details.
