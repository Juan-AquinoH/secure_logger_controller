#  Secure Logger Controller – Proposal Summary

**Designer:** Juan Carlos Aquino Hernández  
**Email:** [juancarlos.aquino@utnay.edu.mx](mailto:juancarlos.aquino@utnay.edu.mx)  
**Institution:** Universidad Tecnológica de Nayarit (UTNAY)  

---

##  Problem & Outcome

In **medical wearable devices**, data reliability during power interruptions is critical. Conventional **volatile memories** lose vital signs data when energy is interrupted.

**Outcome:**  
Development of a **secure, low-power Medical Event Logger SoC** using **ReRAM non-volatile memory** to ensure **data persistence and integrity** even during unexpected power failures.

---

##  Approach (Why NVM?) & What’s Novel

Unlike **Flash** or **SRAM**, **ReRAM NVM** provides **persistent storage** with:
- Ultra-low write energy  
- No standby power consumption  
- High endurance and retention  

Our design integrates **BM Labs ReRAM IP** within the **Caravel open-source SoC**, featuring a **custom Secure Logger Controller (FSM)** that manages:
- FIFO buffering  
- Fault detection  
- Secure event writes  

**Novelty:**  
> First open-source Caravel-based medical logger leveraging ReRAM for real-time fail-safe logging at the edge.

---

##  Performance Targets

| **Metric**                 |         **Target**                          | **Description**                        |
|----------------------------|---------------------------------------------|-----------------------------------------|
| **Write Energy**           | `< 1 µJ per 8-bit event`                    | Ultra-low energy per logged event       |
| **Data Retention**         | `> 10 years`                                | Long-term persistence of medical data   |
| **Latency (Event → NVM)**  | `< 10 µs`                                   | Fast event-to-memory write time         |
| **Power-Failure Recovery** | `100% data preservation`                    | Guaranteed data integrity on power loss |

---

##  Architecture Overview

+-----------------------------------------------------------+
| user_project_wrapper |
| +------------------------+ +---------------------+ |
| | logger_wb_controller | ---> | caravel_top | |
| +------------------------+ +---------------------+ |
| | | |
| +-----------------+ | |
| | secure_logger |-------------------+ |
| +-----------------+ |
| +---------------+ |
| | re_ram_nvm | |
| +---------------+ |
+-----------------------------------------------------------+

yaml
Copiar código

 *Figure 1. Secure Logger Controller integrated into Caravel SoC using ReRAM NVM.*

---

##  Deliverables & Success Metrics

### Deliverables
-  RTL implementation (**SystemVerilog**) compatible with **Caravel/OpenLane**.  
-  Simulation testbench verifying:
  - Logging operation  
  - Power-failure handling  
  - Wishbone interface functionality  
 **GDS-ready** layout for **SkyWater SKY130** tapeout.

### Success Metrics
- 🔹 Functional simulation showing persistent data after power loss.  
- 🔹 Verified ReRAM integration and correct Wishbone protocol operation.  
- 🔹 Clean DRC/LVS results with **<1% area overhead** compared to base Caravel.

---

##  Team

**Name:** Juan Carlos Aquino Hernández  
**Degree Program:** Ingeniería Química  
**Areas of Interest:**  
Semiconductor manufacturing and Artificial Intelligence — with a focus on **semiconductor design, routing processes, and design flow optimization**.  

**Programming Experience:** Limited (Visual C).  
**Goal:** To specialize in **semiconductors and AI**, providing **consulting and academic guidance** in future projects.



##  Next Steps

1. Integrate block diagram figure(s) – suggested format: `docs/figures/block_diagram.png`  s
2. Include simulation waveform or FSM schematic once verified.  
3. Finalize power/performance validation data.

---

 *Developed as part of the Open Hardware initiative at Universidad Tecnológica de Nayarit.*