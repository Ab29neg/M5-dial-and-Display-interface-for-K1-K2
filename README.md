# M5 Dial and Display for K1 & K2

This document provides an overview of the **M5 Dial** and **Display** and **interface** code used for the **K1** and **K2** vehicles in the powertrain integration project.

---

## 📂 Repositories

### 🔘 M5 Dial Code  
**Repository:** [k1poc_powertrain_integration – M5_K2 Folder](https://github.com/Vayve-Mobility-Pvt-Ltd/k1poc_powertrain_integration/tree/main/M5_K2)

- The **M5 Dial** code is common for both **K1** and **K2**.  
- The only difference:
  - **K2:** “AC ON/OFF” text is displayed in **black**.
- Includes the latest feature:
  - Automatically returns to **Neutral** mode if the **VCU** is not sending a valid **drive mode** signal.
- **Note:** When testing without a connected interface, this fallback-to-neutral feature can be observed.

---

### 🖥️ Display (ESP32)
**Repository:** [k1poc_powertrain_integration – display_new Branch](https://github.com/Vayve-Mobility-Pvt-Ltd/k1poc_powertrain_integration/tree/display_new)

- This repository contains the **latest display code flashed in K2**.  
- **K1** may have an older version (not confirmed).  
- The “**Last Updated Time**” text on the display is currently a **dummy value** (not functional and not required).  
- Code updated up to the **“CAN FAULT”** feature:
  - Detects when **OBC**, **BMS**, **DCDC**, or **Motor** are not sending CAN messages.
  - Implements UART checks for **number of bytes transmitted and received**, ensuring no communication glitches.

---

### 🔗 Interface for Display
**Repository:** [k1poc_powertrain_integration – interface_control](https://github.com/Vayve-Mobility-Pvt-Ltd/k1poc_powertrain_integration/tree/interface_control)

- Updated up to the **“CAN FAULT TX”** feature:
  - Transmits CAN fault status if any of the following modules are not sending CAN messages:
    - **OBC**
    - **BMS**
    - **DCDC**
    - **Motor**

---

## 🧭 Summary

| Module     | Repository Branch/Folder | Latest Feature Added                  | Notes |
|-------------|--------------------------|---------------------------------------|-------|
| **M5 Dial** | `main/M5_K2`             | Neutral fallback if VCU inactive      | Same code for K1 & K2 (AC text color differs) |
| **Display** | `display_new`            | CAN Fault detection & UART check      | “Last Updated Time” text is dummy |
| **Interface** | `interface_control`    | CAN Fault TX handling                 | Handles missing CAN signals |

---

**Maintained by:**  
[Vayve Mobility Pvt. Ltd.](https://github.com/Vayve-Mobility-Pvt-Ltd)  
