📌 Overview

This board converts USB signals from a USB Type-C connector into UART TX/RX signals for programming and debugging microcontrollers.
The design follows the CP2102N reference guidelines and includes proper USB-C configuration, ESD protection, decoupling networks, and clean PCB routing.

🧩 Features

USB Type-C (USB 2.0) input

CP2102N-Axx-QFN28 USB–UART converter

TX/RX activity LEDs

ESD protection on D+, D–, CC1, CC2

5.1 kΩ CC resistors for USB-C device mode

Differential pair routing for USB data lines

Thick traces for VBUS and GND

Multiple thermal vias under CP2102N for heat dissipation

2-layer PCB with clean layout

0 ERC and 0 DRC errors in KiCad

🛠 Hardware Components
Component	Description
CP2102N-A01-QFN28	USB–UART bridge IC
USB-C Receptacle (USB 2.0)	Input connector
R1, R2 — 5.1 kΩ	CC1/CC2 pull-downs for device mode
Low-capacitance ESD Diodes	Protection for D+, D–, CC lines
C1, C2 — 100 nF	Decoupling (VREGIN, VDD)
C3, C4 — 100 nF	VBUS filtering
LEDs (D1, D2)	TX/RX indicators
R6, R7 — 470 Ω	LED current limit
J2 Header	TX, RX, RST, GND, VBUS output
🔧 Circuit Description

The USB-C connector provides VBUS (5V), GND, and D+/D– to the CP2102N.
Two 5.1 kΩ resistors on CC1 and CC2 configure the board as a USB device, enabling power negotiation.

D+/D– are routed as a differential pair directly into the CP2102N, protected by low-capacitance ESD diodes.
The chip’s internal LDO outputs 3.3V on VDD, stabilized using 100 nF decoupling capacitors.

TX and RX pins drive activity LEDs using 470 Ω resistors, while the main UART header exposes:

TXD

RXD

RST

VBUS

GND

🖥️ PCB Layout Highlights

2-layer PCB

Clean differential routing for USB D+/D–

Thick traces for VBUS and ground connections

Thin traces for signal lines

Via-in-pad array under CP2102N for thermal relief

Short trace lengths for decoupling capacitors

Shield properly grounded for noise reduction

🧪 Project Workflow

Studied CP2102N datasheet and typical application circuit

Built schematic in KiCad

Selected capacitor/resistor values based on electrical characteristics

Added ESD protection and USB-C configuration resistors

Performed ERC checks → 0 errors

Loaded to PCB editor and routed 2-layer layout

Added thermal vias + power trace width optimization

Performed DRC checks → 0 errors

Generated Gerbers for manufacturing

📁 Repository Structure
├── schematic/          # KiCad schematic files
├── pcb/                # 2-layer PCB layout files
├── gerbers/            # Manufacturing outputs
├── images/             # Renders, plots, screenshots
└── README.md           # Project documentation
