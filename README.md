# vsd-week4
NGSpice Basics and NMOS, PMOS, CMOS


# NgspiceSky130 Full Series Index

## Day 1: Basics of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)

### 1.1 Introduction to Circuit Design and SPICE Simulations
- 1.1.1 Why do we need SPICE simulations?
- 1.1.2 Introduction to basic element in Circuit design – NMOS
- 1.1.3 Strong inversion and threshold voltage
- 1.1.4 Threshold voltage with positive substrate potential

### 1.2 NMOS Resistive Region and Saturation Region of Operation
- 1.2.1 Resistive region of operation with small drain-source voltage
- 1.2.2 Drift current theory
- 1.2.3 Drain current model for linear region of operation
- 1.2.4 SPICE conclusion to resistive operation
- 1.2.5 Pinch-off region condition
- 1.2.6 Drain current model for saturation region of operation

### 1.3 Introduction to SPICE
- 1.3.1 Basic SPICE setup
- 1.3.2 Circuit description in SPICE syntax
- 1.3.3 Define technology parameters
- 1.3.4 First SPICE simulation
- 1.3.5 SPICE Lab with sky130 models

---

## Day 2: Velocity Saturation and CMOS Inverter VTC

### 2.1 SPICE Simulation for Lower Nodes and Velocity Saturation Effect
- 2.1.1 SPICE simulation for lower nodes
- 2.1.2 Drain current vs gate voltage for long and short channel device
- 2.1.3 Velocity saturation at lower and higher electric fields
- 2.1.4 Velocity saturation drain current model
- 2.1.5 Labs Sky130 Id-Vgs
- 2.1.6 Labs Sky130 Vt

### 2.2 CMOS Voltage Transfer Characteristics (VTC)
- 2.2.1 MOSFET as a switch
- 2.2.2 Introduction to standard MOS voltage current parameters
- 2.2.3 PMOS/NMOS drain current v/s drain voltage
- 2.2.4 Step1 – Convert PMOS gate-source-voltage to Vin
- 2.2.5 Step2 & Step3 – Convert PMOS and NMOS drain-source-voltage to Vout
- 2.2.6 Step4 – Merge PMOS-NMOS load curves and plot VTC

---

## Day 3: CMOS Switching Threshold and Dynamic Simulations

### 3.1 Voltage Transfer Characteristics – SPICE Simulations
- 3.1.1 SPICE deck creation for CMOS inverter
- 3.1.2 SPICE simulation for CMOS inverter
- 3.1.3 Labs Sky130 SPICE simulation for CMOS

### 3.2 Static Behavior Evaluation – CMOS Inverter Robustness (Switching Threshold)
- 3.2.1 Switching Threshold, Vm
- 3.2.2 Analytical expression of Vm as a function of (W/L)p and (W/L)n
- 3.2.3 Analytical expression of (W/L)p and (W/L)n as a function of Vm
- 3.2.4 Static and dynamic simulation of CMOS inverter
- 3.2.5 Static and dynamic simulation of CMOS inverter with increased PMOS width
- 3.2.6 Applications of CMOS inverter in clock network and STA

---

## Day 4: CMOS Noise Margin Robustness Evaluation

### 4.1 Static Behavior Evaluation – CMOS Inverter Robustness (Noise Margin)
- 4.1.1 Introduction to noise margin
- 4.1.2 Noise margin voltage parameters
- 4.1.3 Noise margin equation and summary
- 4.1.4 Noise margin variation with respect to PMOS width
- 4.1.5 Sky130 Noise margin labs

---

## Day 5: CMOS Power Supply and Device Variation Robustness Evaluation

### 5.1 Static Behavior Evaluation – CMOS Inverter Robustness (Power Supply Variation)
- 5.1.1 Smart SPICE simulation for power supply variations
- 5.1.2 Advantages and disadvantages using low supply voltage
- 5.1.3 Sky130 Supply Variation Labs

### 5.2 Static Behavior Evaluation – CMOS Inverter Robustness (Device Variation)
- 5.2.1 Sources of variation – Etching process
- 5.2.2 Sources of variation – oxide thickness
- 5.2.3 Smart SPICE simulation for device variations
- 5.2.4 Conclusion
- 5.2.5 Sky130 Device Variation Labs
