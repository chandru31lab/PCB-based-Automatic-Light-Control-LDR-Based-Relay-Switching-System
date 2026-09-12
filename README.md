# 💡 Automatic Light Control & LDR-Based AC Load Switching System

### EasyEDA-Designed Analog Light Sensing, Threshold Detection & Relay Control

> A custom PCB-based automatic light control system that detects ambient light using an LDR and switches an AC bulb through a relay. The circuit uses an LM358 comparator, adjustable threshold control, BC547 transistor driver, flyback protection, and a 5V AC-DC power supply. The complete schematic, PCB layout, 3D model, and hardware prototype were designed using EasyEDA.

[![PCB Design](https://img.shields.io/badge/PCB%20Design-EasyEDA-blue)](https://easyeda.com/)
[![Circuit](https://img.shields.io/badge/Circuit-Analog-green)]()
[![Sensor](https://img.shields.io/badge/Sensor-LDR-orange)]()
[![Comparator](https://img.shields.io/badge/Comparator-LM358-red)]()
[![Driver](https://img.shields.io/badge/Driver-BC547-purple)]()
[![Relay](https://img.shields.io/badge/Output-5V%20Relay-yellow)]()
[![Power](https://img.shields.io/badge/Power-5V%20SMPS-blue)]()

---

## 📌 Overview

The **Automatic Light Control & LDR-Based AC Load Switching System** is an analog electronics project designed to control an AC bulb according to the surrounding light level.

The **LDR (Light Dependent Resistor)** senses ambient illumination. Its resistance changes with light intensity, and a voltage-divider network converts this change into a variable voltage. An **LM358** compares the sensor voltage with an adjustable reference voltage generated using a potentiometer.

The comparator output drives a **BC547 NPN transistor**, which switches a **5V relay**. The relay contacts control the connected AC bulb.

The project was developed from **schematic to physical PCB**, including schematic capture, PCB layout, routing, 3D visualization, fabrication, assembly, and testing using **EasyEDA**.

---

## 🎯 Project Objectives

- Detect ambient light intensity using an LDR
- Convert light variation into a voltage signal
- Compare the sensor voltage against an adjustable threshold
- Drive a relay using a transistor switching stage
- Automatically control an AC bulb/load
- Include relay flyback protection
- Implement the complete design on a custom PCB

---

## 🔄 System Block Diagram

```text
                 AC INPUT
                    │
                    ▼
             ┌─────────────┐
             │  HLK-5M0x   │
             │  AC → 5V DC │
             └──────┬──────┘
                    │
                   +5V
                    │
          ┌─────────┴─────────┐
          │                   │
          ▼                   ▼
    ┌──────────┐       ┌──────────────┐
    │    LDR   │       │ Potentiometer│
    │  Sensor  │       │  Reference   │
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
              ┌─────────┐
              │  Relay  │
              └────┬────┘
                   │
                   ▼
              ┌─────────┐
              │ AC Bulb │
              └─────────┘
```

---

## ⚙️ Working Principle

### 1. Light Sensing

The LDR is the primary sensing element.

```text
Bright Light   → LDR Resistance Decreases
Dark Condition → LDR Resistance Increases
```

The LDR and resistor form a voltage divider, converting the resistance variation into a changing sensor voltage.

### 2. Adjustable Threshold

A **100kΩ potentiometer** generates the reference voltage.

```text
+5V
 │
 ▼
100kΩ POT
 │
 ▼
Reference Voltage
```

Rotating the potentiometer changes the switching threshold, allowing the circuit to be calibrated for the required light level.

### 3. LM358 Comparator

The LM358 compares the **LDR sensor voltage** with the **adjustable reference voltage**.

```text
LDR Sensor Voltage
        VS
Reference Voltage
        ↓
  LM358 Comparator
        ↓
  Switching Output
```

When the sensor voltage crosses the selected reference level, the LM358 output changes state.

### 4. BC547 Relay Driver

The comparator output drives the base of the **BC547 NPN transistor**.

```text
LM358 Output
     ↓
BC547 Base
     ↓
Transistor ON / OFF
     ↓
Relay Coil
```

The transistor acts as the relay driver and provides the required switching current for the relay coil.

### 5. Relay Switching

The energized relay changes its contact state and controls the connected AC bulb/load.

```text
Low-Voltage Control
        ↓
     Relay Coil
        ↓
   Relay Contacts
        ↓
      AC Bulb
```

### 6. Flyback Protection

A **1N4148 diode** is connected across the relay coil to suppress the inductive voltage transient produced when the relay is switched OFF.

```text
Relay OFF
   ↓
Inductive voltage transient
   ↓
Flyback diode provides current path
   ↓
Protects transistor / driver stage
```

---

## 🔌 Power Supply

The control circuit uses an **HLK-5M0x AC-DC power supply module** to obtain a 5V DC supply from the AC input.

```text
AC Mains
   ↓
HLK-5M0x
   ↓
5V DC
   ├── LM358
   ├── LDR Network
   ├── Potentiometer
   ├── BC547
   ├── Relay Coil
   └── LED Indicator
```

> Use the exact power-supply part number printed on the module installed on the final PCB when documenting the hardware.

---

## 🧩 Hardware Components

| Component | Value / Part | Function |
|---|---|---|
| AC-DC Supply | HLK-5M0x | AC to 5V DC conversion |
| Op-Amp | LM358 | Voltage comparison |
| Sensor | LDR / VT90N1 | Ambient light detection |
| Potentiometer | 100kΩ | Adjustable threshold |
| Resistor | 10kΩ | LDR sensing network |
| Transistor | BC547 | Relay driver |
| Relay | SRA-05VDC-CD | AC load switching |
| Diode | 1N4148 | Flyback protection |
| Resistor | 220Ω | LED current limiting |
| LED | LED1 | Status indication |
| Connector | 2-Pin | AC input / bulb connection |

---

## 🧠 Circuit Architecture

```text
POWER SECTION
AC Input → HLK-5M0x → 5V DC

SENSOR SECTION
LDR → Voltage Divider → Sensor Voltage

REFERENCE SECTION
5V → 100kΩ Potentiometer → Reference Voltage

COMPARATOR SECTION
Sensor Voltage + Reference Voltage → LM358

DRIVER / OUTPUT SECTION
LM358 → BC547 → 5V Relay → AC Bulb
```

---

## 🔧 Schematic Design

The complete schematic was designed in **EasyEDA** before PCB implementation.

### Schematic Includes

- AC power input
- AC-DC power supply
- LDR sensing network
- Adjustable reference network
- LM358 comparator
- BC547 transistor driver
- 5V relay
- Flyback protection diode
- LED indicator
- AC bulb output connector

### Signal Flow

```text
Ambient Light
      ↓
     LDR
      ↓
Voltage Divider
      ↓
Sensor Voltage
      ↓
LM358 Comparator
      ↓
BC547 Driver
      ↓
5V Relay
      ↓
AC Load
```

---

## 🖥️ PCB Design Using EasyEDA

The complete PCB was designed using **EasyEDA**.

### Design Workflow

```text
Circuit Concept
      ↓
Schematic Capture
      ↓
Footprint Assignment
      ↓
Component Placement
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
      ↓
Hardware Testing
```

### PCB Design Features

- Custom PCB layout
- Through-hole component implementation
- Dedicated AC input terminal
- Dedicated bulb output terminal
- Relay footprint
- SMPS footprint
- LM358 DIP package
- LDR placement
- Potentiometer placement
- LED status indicator
- Power and signal routing
- Component reference labels
- 3D PCB visualization

---

## 🏗️ Hardware Development

### Stage 1 — Schematic

The complete circuit was designed and interconnected in EasyEDA.

### Stage 2 — PCB Layout

Components were positioned according to electrical connections and board constraints.

### Stage 3 — Routing

The PCB was routed to connect the power, sensing, comparator, driver, and relay sections.

### Stage 4 — 3D Verification

The EasyEDA 3D viewer was used to verify component placement and mechanical arrangement before fabrication.

### Stage 5 — Fabrication

The finalized PCB layout was used to manufacture the physical board.

### Stage 6 — Assembly

The SMPS, relay, LM358, LDR, BC547, diode, resistors, potentiometer, LED, and connectors were assembled on the PCB.

### Stage 7 — Testing

The assembled prototype was tested by changing the light level over the LDR and adjusting the potentiometer to verify the switching response.

---

## 🧪 Testing Procedure

```text
1. Power the circuit
        ↓
2. Verify 5V DC supply
        ↓
3. Expose the LDR to light
        ↓
4. Cover the LDR gradually
        ↓
5. Observe sensor response
        ↓
6. Adjust the potentiometer
        ↓
7. Verify comparator output
        ↓
8. Verify BC547 switching
        ↓
9. Observe relay operation
        ↓
10. Verify AC load switching
```

---

## 📊 Operating Logic

The exact ON/OFF behavior depends on the comparator input polarity and LDR divider arrangement.

For a typical automatic night-light configuration:

| Light Condition | LDR Resistance | Desired Bulb State |
|---|---|---|
| Bright | Low | OFF |
| Low Light | Increasing | Transition |
| Dark | High | ON |

The switching point can be adjusted using the potentiometer.

---

## 📐 Key Electronics Concepts

### Voltage Divider

Converts the LDR resistance change into a measurable voltage.

### Comparator

The LM358 compares the sensor voltage with an adjustable reference.

### Transistor Switching

The BC547 operates as a switching device for the relay coil.

### Flyback Protection

The diode suppresses the relay's inductive voltage transient during turn-off.

### Relay Interface

The relay provides the interface between the low-voltage control circuit and the AC load.

### AC-DC Conversion

The HLK module provides the required 5V DC control supply.

---

## 🛠️ Technologies & Skills

### Electronics

- Analog Electronics
- LDR Sensor Interfacing
- Voltage Divider Design
- Comparator Circuits
- Op-Amp Applications
- Transistor Switching
- Relay Driver Design
- Flyback Protection
- LED Current Limiting

### PCB Design

- EasyEDA
- Schematic Capture
- PCB Layout
- Component Placement
- Footprint Selection
- PCB Routing
- Design Verification
- 3D PCB Visualization
- PCB Fabrication
- PCB Assembly

### Hardware

- LM358
- BC547
- LDR
- 5V Relay
- AC-DC SMPS
- 1N4148 Diode
- Potentiometer
- LED

---

## 📁 Repository Structure

```text
PCB-based-Automatic-Light-Control-LDR-Based-Relay-Switching-System/
│
├── README.md
├── Schematic/
├── PCB/
├── 3D_Model/
├── Hardware/
└── Documentation/
```

> Update the folder and file names above to match the actual repository contents.

---

## 📷 Project Images

The project can be documented through the following development stages:

```text
Schematic
   ↓
PCB Layout
   ↓
3D PCB Model
   ↓
Fabricated PCB
   ↓
Assembled Hardware
```

Recommended documentation images:

- `Schematic.png`
- `PCB_Layout.png`
- `PCB_3D_View.png`
- `Assembled_PCB.jpg`

---

## 🚀 Future Improvements

- Add hysteresis to prevent relay chattering near the switching threshold
- Add adjustable ON/OFF delay
- Add LCD/OLED display for light-level indication
- Add microcontroller-based digital sensing
- Add ESP32-based IoT monitoring
- Add mobile notifications and remote control
- Add cloud data logging
- Replace the mechanical relay with an SSR for silent switching
- Add fuse and over-current protection
- Improve enclosure and mains isolation
- Add automatic day/night calibration

---

## 💼 Applications

- Automatic night lamps
- Street-light control
- Home lighting automation
- Corridor lighting
- Garden lighting
- Outdoor lighting systems
- Parking-area lighting
- Energy-saving lighting systems
- Light-dependent switching applications

---

## ⚠️ Safety Warning

> **This project contains an AC mains switching section.**

The relay contacts and AC terminals may carry dangerous mains voltage.

When operating the circuit with mains voltage:

- Use proper insulation and an appropriate enclosure
- Maintain adequate creepage and clearance
- Use correctly rated terminals, wires, and relay contacts
- Use suitable fuse/protection
- Disconnect mains power before modifying or debugging the circuit
- Never touch the PCB while connected to live mains

**Only perform mains-voltage testing with appropriate electrical knowledge and safety precautions.**

---

## 📌 Key Learning Outcomes

```text
Circuit Analysis
      ↓
Analog Sensor Design
      ↓
Voltage Divider
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
```

This project demonstrates the complete workflow from an electronic circuit concept to a fabricated and assembled PCB prototype.

---

## 🎯 Project Highlights

- Designed an analog LDR-based light sensing circuit
- Implemented adjustable threshold detection
- Used LM358 as the comparator stage
- Designed a BC547-based relay driver
- Added flyback protection for the relay
- Implemented AC load switching
- Designed the complete PCB using EasyEDA
- Created and verified the PCB in 3D
- Fabricated and assembled the physical prototype
- Tested the light-dependent switching operation

---

## 📌 Project Summary

> **An EasyEDA-designed automatic light control system using an LDR, LM358 comparator, BC547 transistor, and 5V relay to detect ambient light and control an AC bulb. The project covers analog sensing, threshold comparison, transistor switching, relay interfacing, protection circuitry, PCB layout, fabrication, assembly, and hardware testing.**

---

## 👤 Author

**Ramachandru**  
B.Tech Electronics & Communication Engineering

**Analog Electronics | Embedded Systems | PCB Design | IoT**

---
