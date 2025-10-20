# Secure Logger Controller
Secure Logger Controller – Proposal Summary
 Designer: Juan Carlos Aquino Hernández
 Email: juancarlos.aquino@utnay.edu.mx
 Institution: Universidad Tecnológica de Nayarit (UTNAY)
 Problem & Outcome
 In medical wearable devices, data reliability under power loss is critical. Conventional volatile memories lose vital
 signs data when energy is interrupted. Outcome: A secure, low-power Medical Event Logger SoC using ReRAM
 non-volatile memory to ensure data persistence and integrity even during power failures.
 Approach (Why NVM?) & What’s Novel
 Unlike Flash or SRAM, ReRAM NVM provides persistent storage with ultra-low write energy and no standby
 power. Our design integrates BM Labs ReRAM IP within the Caravel open-source SoC using a custom Secure
 Logger Controller (FSM) that manages FIFO buffering, fault detection, and secure writes. Novelty: First
 open-source Caravel-based medical logger leveraging ReRAM for real-time fail-safe logging at the edge.
 Performance Targets
 Metric
 Write energy
 Target
 < 1 µJ per 8-bit event
 Data retention
 Latency (event to NVM)
 Power-failure recovery
 Architecture Overview
 >10 years (ReRAM)
 <10 µs
 100% data preservation
 +-----------------------------------------------------------+
 | user_project_wrapper |
 | +------------------------+ +---------------------+ |
 | | logger_wb_controller | ----> | caravel_top | |
 | +------------------------+ | +-----------------+ | |
 | | | secure_logger | | |
 | | +-----------------+ | |
 | | +---------------+ | |
 | | | re_ram_nvm | | |
 | | +---------------+ | |
 +-----------------------------------------------------------+
 Deliverables & Success Metrics
 Deliverables:
 • RTL implementation (SystemVerilog) compatible with Caravel/OpenLane.
 • Simulation testbench verifying logging, power-failure handling, and Wishbone interface.
• GDS-ready design for SkyWater SKY130 tapeout.
 Success Metrics:
 • Functional simulation showing persistent data after power loss.
 • Successful ReRAM memory integration and Wishbone operation.
 • Clean DRC/LVS with <1% area overhead from base Caravel.
 Team
 Name: Juan Carlos Aquino Hernández
 Degree program: Ingeniería Química
 Areas of Interest: Semiconductor manufacturing and Artificial Intelligence, with a strong interest in
 semiconductor design, focusing on routing processes and design flow optimization.
 Previous programming experience: Little in Visual C.
 Additional information: To specialize in semiconductors and AI and to be able to provide consulting and impart
 knowledge to students
