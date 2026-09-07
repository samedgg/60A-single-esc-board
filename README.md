# Single ESC Board (AT32F421)

This project is a compact **Single ESC (Electronic Speed Controller)** board designed for brushless motor applications.

---

## ESC Topology

At the core of the power delivery system is a standard 3-phase inverter topology. This architecture allows for precise electronic commutation, enabling smooth, reliable, and efficient control of the BLDC motor's speed and torque.

<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/29fc12c8-d3d1-453f-8d84-372b85a20152" />

### MOSFET Network
The power stage utilizes six high-efficiency Infineon BSC010N04LSI N-channel MOSFETs configured in a standard 3-phase bridge (High-Side and Low-Side half-bridges for phases A, B, and C). Driven by high-frequency PWM signals, this network effectively inverts the DC supply voltage into the sequenced multiphase waveforms required for precise motor commutation, while keeping switching losses and thermal dissipation to a minimum.

### BEMF Network
To facilitate sensorless motor control, the design integrates a Back-Electromotive Force (BEMF) sensing circuit. This precision resistor divider network scales the high-voltage signals from the unenergized (floating) motor phases down to a safe 3.3V logic level. This continuous feedback loop allows the microcontroller's ADC to accurately detect zero-crossing events, enabling the MCU to calculate the exact rotor position and synchronize commutation timing without the need for external Hall-effect sensors.

---

## 3D Views and Schematic
<img width="837" height="707" alt="3d" src="https://github.com/user-attachments/assets/1e40d190-d179-4e17-899d-a5a682a28c3e" />
<img width="837" height="707" alt="3d back" src="https://github.com/user-attachments/assets/3e041079-3a87-45d4-988d-138cf4500274" />
<img width="3509" height="2481" alt="schematic" src="https://github.com/user-attachments/assets/49298664-a827-45a4-b934-f81a8412bc6c" />

---

## Layers

<img width="873" height="730" alt="layers" src="https://github.com/user-attachments/assets/eee588a3-0d5c-436e-9579-ccc6b7698f65" />


<img width="931" height="790" alt="l1" src="https://github.com/user-attachments/assets/a2433b21-d052-430a-94aa-87353e5dd487" />


<img width="944" height="780" alt="l2" src="https://github.com/user-attachments/assets/dd4a593c-e7e7-45f4-b24e-4735d63479bd" />


<img width="886" height="777" alt="l3" src="https://github.com/user-attachments/assets/2bcd956f-5246-4598-b6c6-cafc9361c720" />


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

---

## IPC-2152 Analysis

Based on IPC-2152 standards evaluated via the Saturn PCB Toolkit, the continuous current-carrying capacity of this Single ESC board is rated at ~24.4A. This theoretical limit is determined by analyzing the narrowest bottleneck of the power delivery network (138 mils), which utilizes two parallel copper layers (L1 and L3) with a 2oz base copper weight.

<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/f8a63d0b-fb8e-489c-8c43-81c377e649b1" />

<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/34e0832c-17e5-437d-ad5a-c575bdc73f60" />

