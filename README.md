# 💡 Automatic Light Control & LDR-Based Relay Switching System

### EasyEDA-Designed Analog Light Sensing and Automatic AC Load Control

> A complete analog electronics project that detects ambient light intensity using an LDR and automatically controls an AC bulb through a relay. The system uses an LM358 comparator, adjustable threshold control, BC547 transistor driver, flyback protection, and a 5V AC-DC SMPS. The complete schematic, PCB layout, 3D PCB model, and physical hardware were designed and developed using EasyEDA.

[![PCB Design](https://img.shields.io/badge/PCB%20Design-EasyEDA-blue)](https://easyeda.com/)
[![Circuit](https://img.shields.io/badge/Circuit-Analog-green)]()
[![Sensor](https://img.shields.io/badge/Sensor-LDR-orange)]()
[![Comparator](https://img.shields.io/badge/Comparator-LM358-red)]()
[![Transistor](https://img.shields.io/badge/Driver-BC547-purple)]()
[![Relay](https://img.shields.io/badge/Output-5V%20Relay-yellow)]()
[![Power](https://img.shields.io/badge/Power-5V%20SMPS-blue)]()
[![Application](https://img.shields.io/badge/Application-Automatic%20Lighting-lightgrey)]()

---

## 📌 Overview

The **Automatic Light Control & LDR-Based Relay Switching System** is an analog light-sensing circuit designed to automatically switch an AC load based on ambient illumination.

The system uses an **LDR (Light Dependent Resistor)** as the light sensor. The resistance of the LDR varies with the intensity of incident light. This resistance variation is converted into a voltage using a voltage-divider network.

An **LM358 operational amplifier** is configured as a comparator to compare the LDR sensing voltage with an adjustable reference voltage generated using a potentiometer.

The comparator output drives a **BC547 NPN transistor**, which controls the coil of a **5V relay**. The relay contacts are then used to switch an external AC bulb.

The complete project was taken from **circuit design to physical PCB implementation**, including schematic capture, PCB layout, routing, 3D visualization, fabrication, component assembly, and testing using **EasyEDA**.

---

## 🎯 Project Objective

The main objective of this project is to develop a simple, low-cost, and reliable automatic lighting controller that can:

- Detect changes in ambient light intensity
- Convert light variations into an electrical signal
- Compare the sensed voltage with an adjustable threshold
- Drive a relay based on the detected light condition
- Automatically control an AC bulb
- Provide visual switching indication
- Implement the complete circuit on a custom PCB

---

## 🔄 System Block Diagram

                 AC MAINS
                    │
                    ▼
             ┌─────────────┐
             │  HLK-5M05   │
             │ AC → 5V DC  │
             └──────┬──────┘
                    │
                   +5V
                    │
          ┌─────────┴─────────┐
          │                   │
          ▼                   ▼
    ┌──────────┐       ┌──────────────┐
    │    LDR   │       │ Potentiometer│
    │  Sensor  │       │   Reference  │
    └────┬─────┘       └──────┬───────┘
         │                    │
         ▼                    ▼
    Sensor Voltage       Reference Voltage
         │                    │
         └─────────┬──────────┘
                   ▼
            ┌─────────────┐
            │    LM358    │
            │  Comparator │
            └──────┬──────┘
                   │
                   ▼
            ┌─────────────┐
            │    BC547    │
            │  Transistor │
            └──────┬──────┘
                   │
                   ▼
             ┌───────────┐
             │ 5V Relay  │
             └─────┬─────┘
                   │
                   ▼
              ┌─────────┐
              │ AC Bulb │
              └─────────┘
⚙️ Working Principle

The circuit works in four major stages:

Light Detection
      ↓
Voltage Generation
      ↓
Threshold Comparison
      ↓
Relay Switching
1. Light Detection

The LDR is the primary sensing element.

An LDR changes its resistance according to the intensity of light falling on its surface.

Bright Light
     ↓
LDR Resistance Decreases

Dark Environment
     ↓
LDR Resistance Increases

This change in resistance is used to generate a variable voltage.

2. Voltage Divider

The LDR is connected as part of a voltage-divider network.

The voltage divider converts the resistance variation of the LDR into a voltage that can be processed by the LM358.

The approximate divider relationship is:

Vout = Vin × R2 / (R1 + R2)

The actual sensing voltage depends on the resistance of the LDR and the fixed resistor connected with it.

Therefore:

Light Intensity
      ↓
LDR Resistance
      ↓
Sensor Voltage
3. Adjustable Threshold

A potentiometer is used to generate an adjustable reference voltage.

By rotating the potentiometer, the switching threshold of the circuit can be changed.

This allows the user to adjust the light level at which the relay changes state.

Potentiometer
      ↓
Reference Voltage
      ↓
LM358 Comparator

This makes the circuit more flexible than a fixed-threshold light sensor.

4. LM358 Comparator

The LM358 compares two voltage levels:

LDR Sensor Voltage
        VS
Reference Voltage

Depending on the relationship between these voltages, the LM358 output changes state.

Sensor Voltage > Reference
          OR
Sensor Voltage < Reference
          ↓
     LM358 Output
          ↓
     BC547 Driver

The comparator therefore acts as the decision-making stage of the circuit.

5. BC547 Relay Driver

The LM358 output drives the base of the BC547 NPN transistor.

The transistor is used as a switching device because the relay coil requires more current than the comparator output should directly provide.

LM358 Output
     ↓
BC547 Base
     ↓
BC547 switches ON/OFF
     ↓
Relay Coil

When the BC547 turns ON, current flows through the relay coil and the relay changes its contact state.

6. Relay Switching

The 5V relay provides the interface between the low-voltage control circuit and the AC load.

5V Control Circuit
       ↓
    Relay Coil
       ↓
 Relay Contacts
       ↓
    AC Bulb

This allows the low-voltage electronics to control an external AC load.

7. Flyback Protection

A 1N4148 diode is connected across the relay coil.

The relay coil is an inductive load. When the transistor switches the relay OFF, the collapsing magnetic field can generate a high-voltage transient.

The diode provides a path for this transient current and protects the transistor and control circuit.

Relay Coil
    │
    ├──── D1 ────┤
    │  1N4148    │
    └────────────┘
🔌 Power Supply

The circuit is powered using an HLK-5M05 AC-DC power supply module.

AC Mains
   │
   ▼
HLK-5M05
   │
   ▼
5V DC
   │
   ├── LM358
   ├── LDR sensing circuit
   ├── Potentiometer
   ├── BC547
   ├── Relay coil
   └── LED indicator

The HLK module provides the required low-voltage DC supply for the control circuit.

🧩 Hardware Components
Component	Value / Part	Purpose
AC-DC SMPS	HLK-5M05	Converts AC mains to 5V DC
Op-Amp	LM358	Voltage comparison
Sensor	LDR / VT90N1	Ambient light detection
Potentiometer	100kΩ	Adjustable threshold
Resistor	10kΩ	LDR voltage divider
Transistor	BC547	Relay driver
Relay	SRA-05VDC-CD	AC load switching
Diode	1N4148	Relay flyback protection
Resistor	220Ω	LED current limiting
LED	LED1	Circuit status indication
Terminal	2-Pin	AC input / bulb output
🧠 Circuit Architecture

The complete circuit can be divided into the following functional blocks:

Power Section
AC Input
   ↓
HLK-5M05
   ↓
+5V DC
Sensor Section
LDR
 ↓
Voltage Divider
 ↓
Variable Sensor Voltage
Reference Section
+5V
 ↓
100kΩ Potentiometer
 ↓
Adjustable Reference Voltage
Comparator Section
Sensor Voltage
      ↓
     LM358
      ↑
Reference Voltage
Driver Section
LM358 Output
      ↓
    BC547
      ↓
 Relay Coil
Output Section
Relay Contacts
      ↓
   AC Bulb
🔧 Schematic Design

The circuit schematic was designed and verified in EasyEDA before PCB implementation.

The schematic contains:

AC power input
AC-DC power supply
LDR sensing network
Adjustable reference network
LM358 comparator
BC547 transistor driver
Relay switching stage
Flyback protection diode
LED indicator
AC bulb output terminal
Signal Flow
Ambient Light
      ↓
      LDR
      ↓
Voltage Divider
      ↓
Variable Voltage
      ↓
LM358 Comparator
      ↓
BC547
      ↓
5V Relay
      ↓
AC Load
🖥️ PCB Design Using EasyEDA

The complete PCB was designed using EasyEDA.

The design process included:

Circuit Design
     ↓
Schematic Capture
     ↓
Component Selection
     ↓
Footprint Assignment
     ↓
PCB Placement
     ↓
PCB Routing
     ↓
Design Verification
     ↓
3D Visualization
     ↓
PCB Fabrication
     ↓
Component Assembly
PCB Design Features
Custom PCB layout
Through-hole components
Dedicated AC input terminal
Dedicated bulb output terminal
Relay footprint
SMPS footprint
LM358 DIP package
LDR placement
Potentiometer placement
LED status indicator
Routed signal and power traces
Component reference labels
3D PCB visualization
🏗️ PCB Development

The project was implemented through the following hardware development stages:

Stage 1 — Schematic

The complete circuit was designed and interconnected in EasyEDA.

Stage 2 — PCB Layout

Components were positioned according to their electrical and mechanical requirements.

Stage 3 — Routing

The PCB traces were routed to connect the power, sensing, comparator, driver, and relay sections.

Stage 4 — 3D Verification

The EasyEDA 3D viewer was used to verify component placement and board appearance before fabrication.

Stage 5 — Fabrication

The PCB layout was converted into a physical PCB.

Stage 6 — Assembly

Components including the SMPS, relay, LM358, LDR, BC547, diode, resistors, potentiometer, and LED were assembled onto the board.

Stage 7 — Testing

The assembled circuit was tested by changing the light intensity over the LDR and adjusting the potentiometer to verify the switching response.

🧪 Testing Procedure

The prototype can be tested using the following procedure:

1. Power the circuit
        ↓
2. Verify 5V DC supply
        ↓
3. Expose LDR to light
        ↓
4. Gradually cover the LDR
        ↓
5. Observe sensor response
        ↓
6. Adjust potentiometer
        ↓
7. Observe LM358 output
        ↓
8. Verify BC547 switching
        ↓
9. Observe relay operation
        ↓
10. Verify AC bulb switching

The potentiometer allows the switching threshold to be adjusted according to the required lighting condition.

📊 Expected Operation

The switching behavior depends on the comparator input configuration and the orientation of the LDR voltage divider.

A typical automatic lighting configuration is:

Light Condition	LDR Resistance	Relay	Bulb
Bright	Low	OFF	OFF
Low Light	Higher	Depends on threshold	Depends on threshold
Dark	High	ON	ON

The exact transition point can be adjusted using the potentiometer.

📐 Important Circuit Concepts

This project demonstrates several fundamental electronics concepts:

Voltage Divider

The LDR is used with a resistor to convert resistance variation into voltage.

Comparator

The LM358 compares the sensor voltage against an adjustable reference.

Transistor Switching

The BC547 works as a switch to control the relay coil.

Flyback Protection

The diode protects the transistor from relay coil back-EMF.

Relay Isolation

The relay provides an interface between the low-voltage control circuit and the AC load.

AC-DC Conversion

The HLK-5M05 converts the AC input into the required 5V DC supply.

🛠️ Technologies & Skills
Electronics
Analog Electronics
LDR Sensor Interfacing
Voltage Divider Design
Comparator Circuits
Op-Amp Applications
Transistor Switching
Relay Driver Design
Flyback Protection
LED Current Limiting
PCB Design
Schematic Capture
PCB Layout
Component Placement
PCB Routing
Through-Hole PCB Design
Footprint Selection
Design Verification
3D PCB Visualization
PCB Fabrication
PCB Assembly
Software
EasyEDA
Hardware
LM358
BC547
LDR
Relay
AC-DC SMPS
Diode
Potentiometer
LED
📁 Repository Structure
Automatic-Light-Control/
│
├── README.md
│
├── Schematic/
│   └── Automatic_Light_Sensor_Schematic.pdf
│
├── PCB/
│   ├── PCB_Layout.png
│   └── PCB_3D_View.png
│
├── Hardware/
│   └── Assembled_PCB.jpg
│
└── Documentation/
    └── Project_Details.pdf

File names can be changed according to the actual files uploaded to the repository.

📷 Project Images

The repository includes images showing the complete development process:

Schematic
    ↓
PCB Layout
    ↓
3D PCB Model
    ↓
Fabricated PCB
    ↓
Assembled Hardware

Recommended images to include:

Schematic.png
PCB_Layout.png
PCB_3D_View.png
Assembled_PCB.jpg
🚀 Future Improvements

The current analog design can be further improved by adding:

🌙 Automatic night-light mode
⏱️ Adjustable ON/OFF time delay
🔄 Hysteresis to prevent relay chattering
📊 Digital light intensity measurement
📟 LCD/OLED display
📡 ESP32-based IoT monitoring
📱 Mobile application control
☁️ Cloud data logging
🔌 Solid-state relay for silent switching
⚡ Fuse and over-current protection
🛡️ Improved mains isolation and enclosure
🔋 Battery backup option
💼 Applications

This type of circuit can be used for:

Automatic street lights
Home lighting automation
Corridor lighting
Garden lights
Outdoor lighting
Energy-saving lighting systems
Automatic night lamps
Light-dependent switching systems
Industrial light-control applications
⚠️ Safety Warning

WARNING: This project contains an AC mains switching section.

The relay contacts and AC terminals may carry dangerous mains voltage.

When operating the circuit with an AC bulb:

Use proper insulation.
Maintain adequate PCB creepage and clearance.
Use appropriately rated terminals and wires.
Use suitable fuse/protection.
Place the PCB inside a proper insulated enclosure.
Never touch the PCB while connected to live mains.
Disconnect AC power before modifying or debugging the hardware.
Ensure the relay contact rating is suitable for the connected load.

The low-voltage control section should be treated separately from the mains switching section.

📌 Key Learning Outcomes

This project provided practical experience in:

Circuit Analysis
      ↓
Analog Sensor Design
      ↓
Comparator Design
      ↓
Transistor Switching
      ↓
Relay Interface
      ↓
PCB Design
      ↓
PCB Routing
      ↓
Hardware Assembly
      ↓
Testing & Debugging

It demonstrates the complete transition from an electronic circuit concept to a working physical PCB prototype.

📈 Project Highlights
Designed a complete analog light-sensing circuit
Implemented an LDR-based ambient light detection system
Used LM358 as a voltage comparator
Designed a BC547-based relay driver
Added flyback protection for the relay
Implemented adjustable light threshold control
Designed the complete PCB using EasyEDA
Created and verified the PCB in 3D
Fabricated and assembled the physical PCB
Tested the circuit using an AC bulb load
📌 Project Summary

An EasyEDA-designed automatic light control system that uses an LDR-based voltage divider, LM358 comparator, adjustable threshold control, BC547 transistor driver, and 5V relay to detect ambient light and control an AC bulb. The project covers the complete electronics development cycle from schematic design and PCB layout to fabrication, assembly, and hardware testing.

👤 Author

Ramachandru

B.Tech Electronics & Communication Engineering

Skills:
Analog Electronics · Embedded Systems · PCB Design · EasyEDA · Circuit Design · Hardware Prototyping
