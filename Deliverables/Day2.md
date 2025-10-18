1. Here I observed the graph for Id vs Vds for different Values of Vgs.
2. Observed the fraph for Id vs Vgs for a single Vds value.

```
**CASE 1 code**

*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description



XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15

R1 n1 in 55

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run
display
setplot dc1
.endc

.end

```

**PLOT:**

<img width="1363" height="654" alt="day2_vds" src="https://github.com/user-attachments/assets/3d636447-96e9-4085-acb1-cf66a5fda4d7" />


```

**CASE2 netlist Code**

*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description

XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15

R1 n1 in 55

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op
.dc Vin 0 1.8 0.1 

.control

run
display
setplot dc1
.endc

.end

```

**PLOT**

<img width="1363" height="654" alt="day2_vgs_plot" src="https://github.com/user-attachments/assets/d8be7aac-7752-45c3-a766-0890f07a2e6f" />

