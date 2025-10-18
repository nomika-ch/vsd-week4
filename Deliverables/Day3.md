
Here transient analysis and VTC under variation is observed:

```
**Transient analysis**

*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description


XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=0.84 l=0.15
XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15


Cload out 0 50fF

Vdd vdd 0 1.8V
Vin in 0 PULSE(0V 1.8V 0 0.1ns 0.1ns 2ns 4ns)

*simulation commands

.tran 1n 10n

.control
run
.endc

.end


```
**PLOT COMMAND**

<img width="1363" height="654" alt="day3_trans_comm" src="https://github.com/user-attachments/assets/f46d5093-7bb5-4559-b245-2407c5e07f0a" />


**PLOT**

<img width="1003" height="644" alt="day3_trans" src="https://github.com/user-attachments/assets/397ceece-6092-4919-9b36-fd2f42d113d5" />



```

**Voltage Transfer Charateristics under variation**

*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description


XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=0.84 l=0.15
XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15


Cload out 0 50fF

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op

.dc Vin 0 1.8 0.01

.control
run
setplot dc1
display
.endc

.end

```

**PLOT**

<img width="1363" height="654" alt="day3_vts_plot" src="https://github.com/user-attachments/assets/954e7533-8e72-4b0a-a1d4-8e60fa0f9606" />

