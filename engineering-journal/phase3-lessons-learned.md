# Phase 3: Hardware Diagnostics & Lessons Learned

demo for pr

Following the studio's core requirement of documenting structural setbacks, this log details how our hardware implementation phase deviated from our mathematical assumptions.

## 1. Hardware Verification Setup
*   **Signal Source:** Function Generator producing a $10\text{kHz}$ Sine Wave at $\pm 12\text{V}$.
*   **Measurement Tools:** Rigol Digital Storage Oscilloscope (DSO), Keysight Digital Multimeter (DMM).
*   **Target Board:** Breadboard assembly of Stage 1 and Stage 2 networks.

## 2. The Failure Mode (Diagnostic Thinking Loop)
*   **Symptom:** Upon initializing the $9\text{V}$ raw rail, the Zener diode (BZX55C3V3) grew hot to the touch ($>85^\circ\text{C}$ within a minute). The reference rail voltage sagged continuously down to $2.8\text{V}$.
*   **Diagnostic Investigation:** 
    1. *Is it a fabrication error?* We verified component orientations. The Zener was correctly placed in reverse-bias configuration.
    2. *Is it a design flaw?* We checked our localized current path. We calculated $R_{\text{drop}}$ assuming an optimal load of $15\text{mA}$. However, our physical test setup was running without the instrumentation amplifier load connected (Open Circuit condition).
    3. *Physics Root Cause:* In an open circuit condition, all current ($I_{\text{total}}$) was forced directly through the Zener diode itself. Because we rounded down our $R_{\text{drop}}$ resistance choice to a standard $47\Omega$ stock resistor instead of calculating bounds properly, the power dissipation surpassed the device maximum limits:
    
    $$P_z = I_z \cdot V_z \approx 120\text{mA} \cdot 3.3\text{V} = 396\text{mW}$$
    
    This exceeded the thermal safe-operating margin of our small packaging container.

## 3. Corrective Measures & Lessons Learned
*   **Resolution:** We recalculated our safety boundaries and swapped out the $47\Omega$ resistor for a **$220\Omega, 0.5\text{W}$ metal-film resistor**. This throttled the worst-case loop current down to safe parameters. The Zener operating temperature fell to $31^\circ\text{C}$ and output stabilized at $3.32\text{V}$.
*   **Core Studio Lessons Learned:**
    *   **Simulation vs. Reality:** SPICE components operate with infinite virtual heat sinks. Physical prototyping forces immediate consideration of real-world thermodynamic limitations ($P_z$).
    *   **Special-Purpose Application:** Standardizing on Schottky diodes for our clamping sub-circuits successfully eliminated signal lag because they bypass the storage charges inherent to conventional P-N structures.
