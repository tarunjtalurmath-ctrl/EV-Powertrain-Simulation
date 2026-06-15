# EV Powertrain Simulation Model

## Overview
This repository features a backward-facing (quasi-static) EV powertrain simulation designed to evaluate the transient current drawn and track battery State of Charge (SoC) under realistic driving conditions. Driven by the standard FTP-75 drive cycle to simulate typical urban driving with frequent stops and starts, the model translates vehicle tractive forces backward through the mechanical transmission and motor maps to calculate net electrical power demand. Crucially, the system incorporates a regenerative braking algorithm that captures kinetic energy during deceleration, modeling it as a negative current loop that actively recharges the battery pack. This bidirectional load profile is processed through a battery Equivalent Circuit Model (ECM) using Coulomb Counting, accurately mapping real-world energy recovery alongside continuous charge depletion.

## Features
* **Longitudinal Driver Model:** Uses a closed-loop controller (representing the driver) to track the target velocity of the FTP-75 drive cycle by generating acceleration and braking commands.
* **Power Electronics (PWM & H-Bridge):** Implements Pulse Width Modulation (PWM) to control an H-Bridge inverter, modulating the voltage delivered to the electric motor based on driver demands.
* **Bidirectional Power & Regenerative Braking:** Captures kinetic energy during deceleration phases. The H-bridge allows energy to flow backward from the motor, acting as a generator, to recharge the battery pack with a negative current loop.
* **Vehicle Body Dynamics:** Models the physical body of the car, accounting for aerodynamic drag, rolling resistance, gravitational forces, and vehicle mass to simulate true tractive resistance.
* **Battery Current & SoC Tracking:** Features a battery Equivalent Circuit Model (ECM) that calculates the exact current drawn under dynamic loads and uses Coulomb Counting to map the continuous depletion and recovery of the battery charge.

  
## Architecture & Tools
* Software: MATLAB R2026a and Simulink
* Toolboxes:Powertrain Blockset, Simscape

## Simulation Results

The plot below illustrates the dynamic response of the battery State of Charge (SoC) over the course of the driving cycle simulation.
<img width="687" height="552" alt="State_Of_Charge" src="https://github.com/user-attachments/assets/20dd9cf8-ebe1-4e15-871e-b68dafeec497" />

## Key Observations & Data Analysis:
* **Continuous Depletion Phases:** The steady, downward slopes (most notable between t = 500s and t = 2000s) represent sustained power draw where the driver model demands torque, causing the H-bridge to pull continuous current from the battery pack to overcome vehicle body tractive resistance.
  
* **Regenerative Braking Spikes:** The sharp, upward recoveries in the SoC curve (such as the peaks near t = 400s and the aggressive rise after $t = 2100$s) clearly demonstrate the regenerative braking algorithm in action. During these deceleration periods, the motor acts as a generator, pushing negative current back through the H-bridge to successfully recover kinetic energy and recharge the battery.

  



## How to Runn the output folder.
