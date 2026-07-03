# Phase 2: Circuit Schematic & Simulation Analysis

## 1. Circuit Schematic (ASCII Block Architecture)
The circuit consists of a dual-stage architecture: a Biased Clipper network utilizing Schottky diodes to clamp the sensor line, followed by a parallel Shunt Zener regulator.
[Stage 1: Schottky Clipper]              [Stage 2: Zener Regulator]
Vin (+/-12V)                                       Vin_Unstable (9V)
o----[ R_limit: 1k ]----+----o Microcontroller      o----[ R_drop: 220R ]----+----o V_Ref (3.3V)
|      Pin (0.3V - 4.8V)                             |
|                                                    |
--- D_clipping1 (Schottky)                           --- D_Zener (3.3V)
/\  (Anode to 4.5V Rail)                             / \ (Reverse Bias)
---                                                  ---
|                                                    |
+----o GND                                           +----o GND

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/6e9c30fc-f993-479f-827c-353429d74194" />
