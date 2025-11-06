# 🚦 FSM Traffic Light Controller — Verilog & Cadence Implementation
[![Language](https://img.shields.io/badge/Language-Verilog-green)](#)
[![EDA Tool](https://img.shields.io/badge/Tool-Cadence%20Virtuoso-blue)](#)
[![Simulation](https://img.shields.io/badge/Simulation-Functional%20&%20Timing-orange)](#)

**Author:** Mukesh Sekar  
**Course:** ECE571 – VLSI System Design  
**Lab 8 – Finite State Machines (FSM): Traffic Light Controller**  
📧 msekar@colostate.edu  

---

## 🎯 Objective
To design, analyze, and implement a **Finite State Machine (FSM)**-based **Traffic Light Controller** for a **three-way intersection** using a structured six-step FSM design flow.  
The lab focuses on:
- Efficient **state reduction** and **encoding**
- **Excitation table** design with **T flip-flops**
- **Verilog implementation** and **Cadence simulation**
- Realistic **timing control** for multi-direction traffic logic

---

## 🧭 Function Overview
The **TrafficLightControllerFSM** manages lights for **roads A, B, and C**:  
- **Road A:** heavily traveled; includes **green/yellow arrows** for southbound left turns  
- **Road B:** moderate traffic  
- **Road C:** low traffic; lights activate only when a **vehicle sensor** detects presence  

Two timing intervals define system operation:
- `TS` → **short** interval (transition / yellow phases)  
- `TL` → **long** interval (steady green / red phases)  

Inputs: car sensor (C), timer (T)  
Outputs: red/yellow/green signals for each road  
The FSM ensures no conflicting flows and prioritizes throughput for busy lanes.

---

## ⚙️ Six-Step FSM Design Process
1. **Define system states** (s0–s7) for all valid light combinations.  
2. **Draw the state diagram** capturing every input-dependent transition.  
3. **Minimize states** using an **implication chart** to merge equivalent states.  
4. **Assign binary codes** (optimal encoding for minimal logic).  
5. **Build excitation table** using **T flip-flops** for each state bit.  
6. **Derive Boolean equations** and implement logic in Verilog / schematic.

---

## 🧩 Key Boolean Equations


---

## 🧪 Results & Analysis
### ✅ Simulation Scenarios
- **Case 1:** `C=0` (no car on road C) → Road A and B alternate normally; road C remains red.  
- **Case 2:** `C=1` (vehicle detected) → Road C receives a timed green period before returning control to A.  

### 🧩 Observations
- FSM transitions validated correctly for all timing intervals.  
- No **race conditions** observed (synchronous design).  
- **Power and area efficiency** achieved via minimized states and T-FF-based encoding.  

---

## ⚡ Theoretical Insights
- **Race Condition:** occurs when multiple state bits toggle simultaneously and intermediate states appear due to unequal propagation delay. Avoided via synchronous updates and hazard-free logic.
- **State Reduction:** simplifies hardware and power usage.
- **State Assignment:** optimized binary codes reduce combinational logic.
- **Flip-Flop Choice:** T-FFs simplify toggle-type FSMs, ideal for compact state transitions.

---

## 🧰 Tools & Technologies
| Category | Tools Used |
|-----------|------------|
| HDL Design | Verilog |
| Simulation & Schematic | Cadence Virtuoso |
| Analysis | Cadence Spectre / Digital Simulator |
| Hardware Concept | T Flip-Flops, FSM Logic Optimization |
| Visualization | Optional HTML/JS Animation (see `viz/traffic-fsm.html`) |

---

## 🧠 Future Work
- Add **Moore vs Mealy comparison** for timing latency.  
- Implement the FSM on **FPGA** to visualize real-time light switching.  
- Integrate with the **8-bit adder visualization framework** for hybrid educational demos.

---

## 🎬 (Optional) Interactive Animation
You can create an animation under `/viz/traffic-fsm.html` using simple JS or SVG to visualize state transitions and traffic light timing.

Example placeholder:
```html
<div class="intersection">
  <div id="A" class="light green"></div>
  <div id="B" class="light red"></div>
  <div id="C" class="light red"></div>
</div>
<script>/* cycle through states s0–s7 with TS/TL timing */</script>

---

Would you like me to add a **matching `viz/traffic-fsm.html` animation** (like the ripple-carry visualizer, showing cars and signal transitions)?  
I can generate a lightweight interactive demo that runs on GitHub Pages using the same visual style.
