# Low-Resistance Meter (2–200 Ω)

This is my first project.

Portable digital ohmmeter designed for accurate low-resistance measurements. This project covers the full electronic system design, including schematic capture, board layout, input protection, and a display subsystem.

Developed as a coursework project for **Design of Industrial Devices and Measurement Systems 1**.
---

![image](main-board.jpg)

---

## Technical Specifications

| Parameter | Specification |
| :--- | :--- |
| **Measurement Range** | 2 Ω, 20 Ω, and 200 Ω full-scale |
| **Current Source** | 1 mA, 10 mA, and 100 mA (switch-selectable) |
| **Display** | $3\frac{1}{2}$-digit multiplexed LCD (VIM-503-DP-RC-S-HV via MAX1491) |
| **Power Supply** | Single 9 V battery (BT1) with internal +5 V regulation (LM78M05) |
| **Measurement Method** | 4-wire (Kelvin) sensing |
| **Form Factor** | 2-layer $100 \times 100\text{ mm}$ SMD PCB |

---

## Core System Features

* **Precision Current Source:** Dual op-amp (U4/U5) driver feeding a PMOS pass element and dedicated sense resistors to deliver stable excitation currents.
* **4-Wire Sensing:** Separate current ($I+/I-$) and voltage sense ($V+/V-$) terminals eliminate test-lead resistance errors.
* **Instrumentation Front-End:** High-precision INA826 instrumentation amplifier conditions signals for the MAX1491 ADC ($\pm 2\text{ V}$ full-scale).
* **Comprehensive Circuit Protection:**
  * **Power Supply:** PMOS reverse-polarity protection ($R_{DS(on)} = 70\text{ m}\Omega$) and secondary protection diodes on the regulator.
  * **Input & Current Source:** Self-resetting PTC fuses, BAT54S overvoltage clamping diodes, and TVS suppressors for ESD immunity.
* **Continuity / Short-Circuit Indicator:** MAX9031 comparator with 4 mV built-in hysteresis and an adjustable threshold (1 to 50 Ω). Provides both visual (LED) and audible (buzzer) feedback.
* **User Features:** Data HOLD button and low-battery visual warning (`LOWBATT` indicator when $V_{BAT} < 4.7\text{ V}$).

---

## Hardware & PCB Layout

* **Subsystem Separation:** Off-board 9 V battery compartment and daughtercard-mounted LCD display for flexible enclosure integration.
* **Trace Topology:** Dedicated 50 mil power routing and 20 mil signal traces with dual-sided ground planes for reduced EMI and easy grounding.
* **Ergonomics:** Color-coded S16N-PC jack layout designed for intuitive Kelvin clamp connection and edge-mounted user controls.


