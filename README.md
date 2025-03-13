# 🚦 Traffic Light Controller Project

## 📌 Overview
This project implements a **traffic light controller** for a highway and farm road intersection using **Verilog**. The goal is to design a system that efficiently manages traffic signals at the intersection of a **highway and a farm road**, ensuring proper traffic flow and safety.

The system consists of **four traffic signals**:
- **Highway Signal 1**
- **Highway Signal 2**
- **Farm Road Signal 1**
- **Farm Road Signal 2**

### 🔧 Design Approach
- **Finite State Machine (FSM):** The core logic is built using a **state machine** with **18 different states**, each defining specific traffic light behaviors based on a set delay system.
- **Timing & Synchronization:** The system uses **predefined delay values** to regulate transitions between states.
- **ROM-Based Verification:** The design incorporates a **ROM module** to store the expected values for all traffic light states, which are then compared with the actual output to ensure accuracy.
- **Design Validation:** A final verification step is performed using a **testbench**, ensuring that the traffic light transitions work as intended and detecting mismatches between the expected and actual values.

## 🎯 Features
1- **State Machine-Based Control:**
   - Implements a **finite state machine (FSM)** to manage traffic lights.
   - Supports **18 different states** based on a predefined delay system.

2- **Traffic Light Encoding:**
   - 🟢 **Green:** `00`
   - 🟡 **Yellow (when changing from green):** `01`
   - 🔴 **Red:** `10`
   - 🟠 **Red-Yellow (when changing from red):** `11`

3- **Design Verification with ROM:**
   - Stores expected traffic light states in **ROM (Read-Only Memory)**.
   - Compares real-time outputs against expected values.
   - Reports mismatches using a built-in **analyzer module**.

4- **Testbenches for Validation:**
   - **State Machine Testbench:** Ensures logical behavior.
   - **ROM Testbench:** Verifies stored expected values.
   - **Final System Testbench:** Integrates all components and validates performance.

## 🔄 Traffic Light States
The system operates with **18 different states**, each defining a unique traffic signal configuration. The states regulate the flow of vehicles between the **highway** and **farm road** by alternating between green, yellow, and red signals. Below are some key states:

- **S0 (Initial State):** All lights are **red** to ensure a controlled start.
- **S1-S2:** The highway traffic light transitions to **green**, allowing vehicles to pass while farm road lights remain **red**.
- **S3-S5:** The highway light transitions to **yellow** and then **red**, preparing to allow farm road traffic.
- **S6-S8:** The farm road light turns **green**, allowing farm vehicles to move while the highway is stopped.
- **S9-S17:** Alternates between different yellow, red, and red-yellow states, ensuring smooth transitions between the two roads.
- **S17 → S0:** Resets the cycle, returning to an all-red state before starting again.

The system ensures fairness by assigning proper timing delays for each state, optimizing traffic flow and preventing congestion.

## 🏗 Design Philosophy
This design follows a **modular approach** to ensure clarity and efficiency:
1. **State Machine Module:**
   - Implements an **FSM** to handle traffic light transitions.
   - Uses **predefined parameters** for each state and corresponding traffic light behavior.
   - Maintains a **5-bit counter** to control timing for each state.

2. **ROM-Based Verification:**
   - Stores expected traffic light outputs to validate FSM performance.
   - Compares **real-time traffic signals** with stored ROM values to detect errors.

3. **Hierarchical Module Structure:**
   - **State Machine:** Controls traffic light transitions.
   - **ROM Generator:** Stores correct outputs for verification.
   - **Testbenches:** Simulate and validate behavior before implementation.

This structured approach ensures **correct traffic flow**, **proper timing control**, and **reliable verification mechanisms** for the system.

## 🏗 Code Structure
### 1️⃣ **State Machine Module (`state_yaz`)**
- Inputs: `clk`, `rst`, `go`
- Outputs: `hiway1`, `hiway2`, `farm1`, `farm2`
- Implements **FSM logic** for traffic control

### 2️⃣ **Traffic Light Testbench (`traffic_tb`)**
- Simulates state machine behavior
- Prints real-time outputs
- Uses clock signals for state transitions

### 3️⃣ **ROM Module (`generateTests`)**
- Stores **expected traffic light sequences**
- Takes `Address` as input and provides **predefined outputs**

### 4️⃣ **ROM Testbench (`Gen_tb`)**
- Iterates through stored ROM values
- Ensures correct traffic light encoding

### 5️⃣ **Final Integrated System (`final_system`)**
- Combines **state machine** and **ROM verification**
- Reports errors when real outputs **don’t match expected values**

### 6️⃣ **Final System Testbench (`System_tb`)**
- Provides a **complete simulation** of the traffic controller
- Checks synchronization between FSM and ROM

## 🖥 Simulation Results
- **State machine output:** Correct transitions observed.
- **ROM generator output:** Matches expected values.
- **Final system analysis:** Error detection and verification successful.

## 📫 Contact
For any questions or discussions, feel free to reach out:

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:yazedyazedl2020@gmail.com)  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/yazeed-hamdan-59b83b281/)
