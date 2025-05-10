# E3088F Micro-Mouse Power Subsystem

This repository contains the hardware design files for the power subsystem of a Micro-Mouse robot. The project was developed as part of the EEE3088F 2025 course at the University of Cape Town.

## Repository Contents

- `/MM/` – Main schematic and PCB layout files (KiCad 7.0+)
- `/TP5100/` – Additional circuit block for battery charging options
- `README.md` – Project documentation and instructions

## Power Subsystem Overview

The power module is responsible for delivering stable and regulated power to all other subsystems of the Micro-Mouse, including the processor, motors, and sensors. The key responsibilities of the subsystem include:

- **Dual Voltage Regulation:**  
  - 3.3 V rail (±5%) at up to 300 mA  
  - 5 V rail (±5%) at up to 1.5 A  
  Both are regulated from a single-cell 3.7 V lithium-polymer battery using MT3608-based boost conversion.

- **Battery Charging Support:**  
  - Supports charging via USB-C (9 V input)  
  - Two selectable charging modes:  
    - Slow mode (~200 mA)  
    - Fast mode (~600 mA ±100 mA)  
  - Controlled using the TP5100 or similar ICs

- **USB-C Power Negotiation:**  
  - Uses IP2721 PD controller to negotiate 9 V from a USB-C PD host  
  - Compatible with standard USB PD power sources

- **Current and Voltage Monitoring:**  
  - Uses INA219 to monitor battery voltage and current via a 5 mΩ precision shunt resistor  
  - Communicates over I2C (SCL on PB8, SDA on PB9)

- **External Load Switching:**  
  - Provides two high-side switched 5 V outputs  
  - Implemented using the TPS2066DR dual-channel load switch  
  - Each channel supports up to 1 A with current limiting

- **Motor Interface Support:**  
  - Interfaces with up to 4 brushed DC motors  
  - Provides power and control line passthroughs for motor drivers

- **System ON/OFF Control:**  
  - Implements a low-power shutoff mode  
  - Draws <30 μA in OFF state  
  - Full 2 A system current available in ON state

- **PCB Design Constraints:**  
  - Fits within 82 mm × 60 mm footprint  
  - Interfaces via 2x16 pin header to motherboard  
  - Includes JST PH connector for the battery

## How to Use This Repository

1. Clone the repository to your local machine.
2. Open the `.kicad_sch` and `.kicad_pcb` files in KiCad 7.0+.
3. Review the schematic comments to understand functional blocks.
4. Use the BOM and PnP files in `/MM/` to prepare for JLCPCB manufacturing.
5. For charging circuits, consult the `/TP5100/` folder.

## 👤 Authors

**Thobani Blose** & **Batsirai Rwatirera** 
EEE3088F – University of Cape Town, 2025
