# Zero Voltage Switching Circuit

This is an LC tank oscillator circuit which uses two mosfets to feed the damping power to the LC tank...and use the output waveform to drive a High voltage transformer or an Induction heating coil.

---
<img width="1846" height="1175" alt="image" src="https://github.com/user-attachments/assets/2a2a3ba6-15bf-4f2e-9a87-a9a3cccdfef8" />

## Repository Structure

```
├── docs/                   # Datasheet IRFP4468PbF n-channel MOSFET
├── manufacturing/          # Gerbers & BOM
│   ├── gerbers/            # Gerber and drill files for PCB fabrication
│   ├── bom/                # Bill of Materials (.csv )
├── ZVS.kicad_pcb  # KiCad PCB Layout file
├── ZVS.kicad_sch  # KiCad Schematic file
├── ZVS.kicad_pro  # KiCad Project file
└── README.md               # This file
 #Zero Voltage Switching (ZVS) Flyback Driver/Induction Heater
 ```
 This repository contains a KiCad schematic and PCB design for a high-efficiency Mazzilli Zero Voltage Switching (ZVS) Driver. This circuit is widely used for driving high-voltage transformers (like television flybacks), induction heaters, and Tesla coils due to its simplicity, high efficiency, and minimal thermal generation.
 
## **Features**:
  
  Zero Voltage Switching: The MOSFETs switch states only when the voltage across them drops to zero, drastically reducing switching losses and keeping the transistors cool.High-Current Handling: Utilizes heavy-duty IRFP4468PbF N-channel MOSFETs.Robust Gate Protection: Features dual $ Zener diodes and  pull-up resistors to prevent gate overvoltage and ensure rapid switching.
  
## **Circuit Overview & Operating Principle**:
  
  The circuit operates as a self-resonant push-pull oscillator. When power is applied via terminal J1, one MOSFET turns on slightly faster than the other. This imbalances the circuit, initiating a resonant oscillation between the parallel tank capacitors (C1 and C2) and the primary coil of the external transformer connected to J2.The fast diodes (D1 and D2) cross-couple the drains to the opposite gates, turning off one MOSFET as the other's drain voltage drops to zero.Resonant FrequencyThe operational frequency is determined solely by the total tank capacitance and the inductance of the external primary coil you attach to terminal Note: The inductors L1 and L2  act as DC chokes to smooth incoming current and do not affect the resonance frequency. Ensure your power supply can source substantial current  or more depending on your load).PCB Trace Widths: If you are routing this board, ensure the high-current paths (Power -> Input-> Chokes ->MOSFET-> Drains-> Tank ->Capacitors->Output) use very wide traces, thick copper  preferred), or are reinforced with soldered wire.Tank Capacitors: Do not use standard ceramic or cheap film capacitors for C1 and C2. The high ripple currents will quickly overheat and destroy them. Use dedicated resonant induction/MKP capacitors.Thermal Management: Even though ZVS minimizes heat, the MOSFETs will still warm up under continuous high loads. Mount both Q1 and Q2 to substantial heatsinks (isolated with mica/silicone pads if sharing a single heatsink).

## PCB Design:

   The PCB for this build is a two layer top and bottom , and uses through hole components for soldering simplicity.
  <img width="1077" height="750" alt="image" src="https://github.com/user-attachments/assets/f0957ec2-d282-448b-9d88-23eea952c806" />

## 3D Model:
### Rendered 3D Model:
  <img width="1440" height="1144" alt="image" src="https://github.com/user-attachments/assets/70298b9a-96ca-438f-bbe8-8880fcabc7d4" />

### Bare PCB Front(1st Layer):  
  
  <img width="1538" height="1322" alt="image" src="https://github.com/user-attachments/assets/57daa68d-e79e-4763-8cb7-b01cd9c63d5f" />

### Bare PCB Rear(2nd Layer):  
  
  <img width="1718" height="1360" alt="image" src="https://github.com/user-attachments/assets/1015debe-2938-4e52-86bb-f648a213d9e6" />

## ⚠️WARNING:
  
  This circuit is designed to drive high-voltage/high-power components. Depending on the transformer connected to J2, it is capable of generating lethal voltages and currents. Always discharge capacitors before handling the circuit, work in a well-ventilated space, use appropriate personal protective equipment (PPE), and never operate the system unattended. The authors are not responsible for any damage, injury, or loss caused by the construction or operation of this project.
  
## 📄License:
  
  This project is open-source. Feel free to modify, distribute, and use it for your own applications under the GNU License.
