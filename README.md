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

Architecture Description

The Secure Logger SoC architecture is based on the Caravel platform and is designed for low-power embedded systems that require secure event logging in non-volatile memory. It is composed of several interconnected modules that enable secure data capture, storage, and reading even in the event of power interruptions.

1. Inputs

GPIO / Logic Analyzer (LA) Signals:
These enable the SoC to communicate with external devices and monitor internal signals.
They serve as an input interface for commands, sensor data, or event triggers.

2. Core Modules
RISC-V CPU

Main processing core that executes instructions from the RV32I suite (and optionally RV32M for multiplication/division operations).

Controls data flow between peripherals, memory, and the secure logger controller.

Wishbone Bus

Interconnects all SoC modules (CPU, NVM, logging controller).

Facilitates efficient communication between modules and enables consistent access to memory or peripherals.

NVM ReRAM

Highly energy-efficient non-volatile memory.

Persistently stores critical events even during power outages.

Ensures data integrity and recovery after unexpected reboots.
Secure Logger Controller

The SoC's central module ensures the security and consistency of logs.

Manages the writing and reading of data in ReRAM.

Implements protection mechanisms against data corruption or unauthorized access.

3. Outputs

GPIO/LA Signals:
Outputs for sending processed information or logged events to external systems, actuators, or monitoring interfaces.

4. Data Flow

The input signals (GPIO/LA) are captured by the RISC-V CPU.

The CPU processes the information and, if necessary, writes it to NVM ReRAM via the Secure Logger.

The Wishbone Bus facilitates communication between all internal modules.

Finally, processed data or critical events can be sent through the GPIO/LA outputs.
##  Deliverables & Success Metrics

### Deliverables
-  RTL implementation (**SystemVerilog**) compatible with **Caravel/OpenLane**.  
-  Simulation testbench verifying:
  - Logging operation  
  - Power-failure handling  
  - Wishbone interface functionality  
 **GDS-ready** layout for **SkyWater SKY130** tapeout.

### Success Metrics
- Functional simulation showing persistent data after power loss.  
- Verified ReRAM integration and correct Wishbone protocol operation.  
- Clean DRC/LVS results with **<1% area overhead** compared to base Caravel.

---

##  Team

**Name:** Juan Carlos Aquino Hernández  
**Degree Program:** Ingeniería Química  
**Areas of Interest:**  
Semiconductor manufacturing and Artificial Intelligence — with a focus on **semiconductor design, routing processes, and design flow optimization**.  

**Programming Experience:** Limited (Visual C).  
**Goal:** To specialize in **semiconductors and AI**, providing **consulting and academic guidance** in future projects.



##  Next Steps

1. Integrate block diagram figure(s) – suggested format: `docs/figures/block_diagram.png`  
2. Include simulation waveform or FSM schematic once verified.  
3. Finalize power/performance validation data.

--

