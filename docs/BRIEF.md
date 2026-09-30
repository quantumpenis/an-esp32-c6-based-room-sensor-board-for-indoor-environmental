# An ESP32-C6 based room sensor board for indoor environmental monitoring.

An ESP32-C6 based room sensor board for indoor environmental monitoring.

Core functionality:
- Measure temperature and relative humidity using a Sensirion SHT41 sensor over I2C
- Report data wirelessly over Wi-Fi (and optionally Thread/Matter if the ESP32-C6 supports it cleanly)
- Single status LED (preferably addressable or just a simple high-efficiency LED with current-limiting resistor) for power-on, connection status, and error indication
- USB-C connector for both power and firmware flashing / serial console (must support USB Serial/JTAG or native USB CDC if available on the C6)

Power:
- Powered primarily from USB-C (5 V)
- On-board 3.3 V regulation for the ESP32-C6 and sensors
- Clean power path with basic reverse polarity / over-current protection if space allows
- Target average current under 50 mA when actively transmitting, and under 1 mA in deep sleep if feasible

Form factor & construction:
- Strictly 2-layer board
- Maximum outline 50 × 50 mm (prefer smaller if possible, target ~40 × 40 mm)
- Mounting holes for M2 or M2.5 screws near the corners
- Components on one side only if possible for easy assembly
- Keep the USB-C connector on one edge for easy access

Interfaces & pins:
- Break out a few unused GPIO pins + 3.3 V + GND on a small header or test points for future expansion
- I2C bus for the SHT41 must be properly pulled up
- Status LED on a free GPIO with appropriate current limiting

Constraints & non-goals:
- Must use real, currently available parts with known footprints and JLCPCB / LCSC part numbers where possible
- No battery or charging circuit in this revision
- No display, no buttons, no buzzer
- No external antenna (use the PCB antenna or chip antenna already supported by the ESP32-C6 module if using a module)
- Keep the design simple and low-cost; prefer modules over bare chips if it significantly reduces layout risk
- Board must pass ERC and DRC cleanly and be ready for a first prototype order

Deliverables expected:
- Complete KiCad schematic and PCB
- Clear power tree and pinout documentation
- BOM with manufacturer part numbers
- Basic bring-up notes
