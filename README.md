# Bluetooth Speaker 2x3W

This repository contains the hardware design files and documentation for a custom 2x3W Bluetooth Speaker circuit. The board integrates a lithium-ion battery management system, a boost converter, a Bluetooth audio receiver, and a Class-D audio amplifier into a single cohesive PCB. 

## Features

*   **USB-C Charging:** Modern USB Type-C receptacle for power input.
*   **Integrated Battery Management:** Onboard charging and protection circuitry for a single-cell Li-ion battery.
*   **Wireless Audio:** Integrated m18 Bluetooth module for audio streaming.
*   **High-Efficiency Audio Amplification:** Uses a Class-D amplifier capable of driving two 3W speakers.
*   **Stable 5V Power:** Integrated boost converter ensures stable 5V delivery to the audio and Bluetooth circuits regardless of battery voltage.

## Hardware Architecture

The circuit is divided into four main functional blocks:

### 1. USB-C Input & Li-ion Charger
*   Utilizes the TP4056 linear charge management controller.
*   Features dual indicator LEDs (LED_RED for charging, LED_GREEN for standby/full).
*   The USB-C input includes 5.1k pull-down resistors on the CC1 and CC2 lines to request 5V from modern USB-C PD chargers.

### 2. Battery Protection & Power Switch
*   Provides over-charge, over-discharge, and short-circuit protection using the DW01A protection IC.
*   Uses an FS8205A dual N-channel MOSFET (Q1 and Q2) to switch the battery ground.
*   Includes a physical 2-pin connector (J2) for the Li-ion battery.

### 3. 5V Boost Converter
*   Built around the MT3608 high-efficiency step-up converter.
*   A physical slide switch (SW1) sits between the battery output and the boost converter input to power the device on and off.
*   The output voltage is configured to exactly 5.0V using a feedback resistor divider (22kΩ and 3kΩ), following the formula $V_{out} = 0.6V \times (1 + 22k/3k) = 5.0V$.

### 4. Audio Amplifier & Bluetooth Module
*   Powered by the PAM8403D Class-D audio amplifier.
*   Receives audio signals via the onboard m18 Bluetooth receiver module.
*   Left and Right audio channels are AC-coupled through 1uF capacitors (C7 and C9) between the Bluetooth module and the amplifier.
*   Audio output is routed to two screw terminals (J3 for Left, J4 for Right) for easy speaker connection.

## PCB Layout

The PCB layout consolidates all components onto a rectangular board. 
*   The USB-C port is edge-mounted on the left side for external access.
*   The power switch (SW1) is centrally located for user accessibility.
*   The m18 Bluetooth module is mounted on the far right edge to minimize interference with the power electronics.
*   Screw terminals for the left and right speakers are positioned along the top edge of the board.
*   The design utilizes a mix of surface-mount components (SMD) and through-hole parts (modules and connectors).
