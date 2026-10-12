# Bluetooth Speaker 

This repository contains the hardware design files and documentation for a custom Bluetooth Speaker circuit. The board integrates a lithium-ion battery management system, a boost converter, a Bluetooth audio receiver, and a Class-D audio amplifier into a single cohesive PCB. 

## Features

*   **USB-C Charging:** Modern USB Type-C receptacle for power input.
*   **Integrated Battery Management:** Onboard charging and protection circuitry for a single-cell Li-ion battery.
*   **Wireless Audio:** Integrated m18 Bluetooth module for audio streaming.
*   **High-Efficiency Audio Amplification:** Uses a Class-D amplifier capable of driving two 3W speakers.
*   **Stable 5V Power:** Integrated boost converter ensures stable 5V delivery to the audio and Bluetooth circuits regardless of battery voltage.
*   <img width="1359" height="798" alt="image" src="https://github.com/user-attachments/assets/31e91506-29ed-4fb7-9250-badc2674b7fc" />


## Hardware Architecture

The circuit is divided into four main functional blocks:

### 1. USB-C Input & Li-ion Charger
*   Utilizes the TP4056 linear charge management controller.
*   Features dual indicator LEDs (LED_RED for charging, LED_GREEN for standby/full).
*   The USB-C input includes 5.1k pull-down resistors on the CC1 and CC2 lines to request 5V from modern USB-C PD chargers.
*   <img width="944" height="677" alt="Image" src="https://github.com/user-attachments/assets/52dfbde2-2e74-457f-b3c6-c137899cc29a" />

### 2. Battery Protection & Power Switch
*   Provides over-charge, over-discharge, and short-circuit protection using the DW01A protection IC.
*   Uses an FS8205A dual N-channel MOSFET (Q1 and Q2) to switch the battery ground.
*   Includes a physical 2-pin connector (J2) for the Li-ion battery.
*   <img width="804" height="457" alt="Image" src="https://github.com/user-attachments/assets/c155c73b-bd94-4ff1-ba35-2d1e2ab15fdd" />

### 3. 5V Boost Converter
*   Built around the MT3608 high-efficiency step-up converter.
*   A physical slide switch (SW1) sits between the battery output and the boost converter input to power the device on and off.
*   The output voltage is configured to exactly 5.0V using a feedback resistor divider (22kΩ and 3kΩ).
*   <img width="803" height="433" alt="Image" src="https://github.com/user-attachments/assets/5e6dacda-f163-4730-b842-9df27376f05e" />

### 4. Audio Amplifier & Bluetooth Module
*   Powered by the PAM8403D Class-D audio amplifier.
*   Receives audio signals via the onboard m18 Bluetooth receiver module.
*   Left and Right audio channels are AC-coupled through 1uF capacitors (C7 and C9) between the Bluetooth module and the amplifier.
*   Audio output is routed to two screw terminals (J3 for Left, J4 for Right) for easy speaker connection.
*   <img width="873" height="430" alt="Image" src="https://github.com/user-attachments/assets/17eda8c2-4771-405a-b8c4-12f1e6586b60" />

## PCB Layout

The PCB layout consolidates all components onto a rectangular board. 
*   The USB-C port is edge-mounted on the left side for external access.
*   The power switch (SW1) is centrally located for user accessibility.
*   The m18 Bluetooth module is mounted on the far right edge to minimize interference with the power electronics.
*   Screw terminals for the left and right speakers are positioned along the top edge of the board.
*   The design utilizes a mix of surface-mount components (SMD) and through-hole parts (modules and connectors).
*   <img width="1177" height="436" alt="Image" src="https://github.com/user-attachments/assets/dbad12a6-2105-44dd-ae06-736671c9c0b0" />
