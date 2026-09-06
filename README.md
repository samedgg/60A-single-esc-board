# 60A Single ESC Board (AT32F421)

This project is a compact **Single ESC (Electronic Speed Controller)** board designed for FPV drones and brushless motor applications. It handles up to 60A continuous current and uses the AT32F421 microcontroller.

---

## ESC Topology

The system uses a standard 3-phase inverter topology to drive a brushless DC (BLDC) motor. 

<img width="843" height="528" alt="image" src="https://github.com/user-attachments/assets/29fc12c8-d3d1-453f-8d84-372b85a20152" />

### MOSFET Network
The power stage consists of 6 N-channel MOSFETs (Infineon BSC010N04LSI) arranged in a 3-phase bridge configuration (High-Side and Low-Side pairs for phases A, B, and C). These MOSFETs switch rapidly to convert the DC battery voltage into 3-phase AC power for the motor.

### BEMF Network
To run the motor without physical sensors, the board uses a Back-EMF (BEMF) resistor divider network. It scales down the voltage from the floating motor phases to safe levels (3.3V) so the microcontroller's ADC can read the rotor position and time the commutation correctly.

---

## 3D Views and Schematic
<img width="837" height="707" alt="3d" src="https://github.com/user-attachments/assets/1e40d190-d179-4e17-899d-a5a682a28c3e" />
<img width="837" height="707" alt="3d back" src="https://github.com/user-attachments/assets/3e041079-3a87-45d4-988d-138cf4500274" />
<img width="3509" height="2481" alt="schematic" src="https://github.com/user-attachments/assets/49298664-a827-45a4-b934-f81a8412bc6c" />

---

## Layers
<img width="873" height="763" alt="layers" src="https://github.com/user-attachments/assets/eee588a3-0d5c-436e-9579-ccc6b7698f65" />

The PCB uses a 4-layer stack-up optimized for high-current handling and low noise:

**Layer 1 (Top):** Main power traces, motor phase connections, and component placement.
<img width="931" height="790" alt="l1" src="https://github.com/user-attachments/assets/a2433b21-d052-430a-94aa-87353e5dd487" />

**Layer 2 (Plane):** Continuous GND (Ground) plane for return paths and shielding.
<img width="944" height="780" alt="l2" src="https://github.com/user-attachments/assets/dd4a593c-e7e7-45f4-b24e-4735d63479bd" />

**Layer 3 (Signal/Power):** Analog routing and auxiliary power paths.
<img width="886" height="777" alt="l3" src="https://github.com/user-attachments/assets/2bcd956f-5246-4598-b6c6-cafc9361c720" />

**Layer 4 (Bottom):** Duplicate power polygons connected with heavy via stitching to share the 60A current load and reduce heat.
<img width="864" height="785" alt="l4" src="https://github.com/user-attachments/assets/298c4c8f-420a-410a-93bb-1e8ba0749db5" />

---

## Bill of Materials

| Designator | Component | Description |
| :--- | :--- | :--- |
| **U2** | AT32F421G8U7 | 32-bit ARM Cortex-M4 Microcontroller |
| **U1** | DRV8300DPWR | 3-Phase MOSFET Gate Driver |
| **Q1 - Q6** | BSC010N04LSI | 40V N-Channel Power MOSFET |
| **R22** | Shunt Resistor | Low-ohm current sensing resistor |
| **U3-U4** | TPS62933DRLR Buck Regulator | Power inductor for 9V/3.3V regulation |
| **C1 - C20** | SMD Ceramic Capacitors | Decoupling and input filter capacitors |
