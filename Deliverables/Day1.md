**What are Process Corners?**

When ICs are manufactured, transistor parameters like:
-  Threshold voltage (Vth)
-  Carrier mobility (μ)
-  Oxide thickness (Tox)
-  Channel length (L)

do not come out exactly identical on every chip — they vary slightly due to fabrication tolerances.

So, foundries define a few standard corners (sets of transistor models) to simulate these variations.

**The common process corners:**

| Corner | NMOS    | PMOS    | Meaning              | Behavior                                                         |
| :----- | :------ | :------ | :------------------- | :--------------------------------------------------------------- |
| **TT** | Typical | Typical | **Typical Corner**   | Both NMOS & PMOS are at *nominal (average)* process values       |
| **SS** | Slow    | Slow    | **Slow-Slow Corner** | Both transistors are weaker → lower current, slower switching    |
| **FF** | Fast    | Fast    | **Fast-Fast Corner** | Both transistors are stronger → higher current, faster switching |
| **FS** | Fast    | Slow    | **Fast-Slow Corner** | NMOS faster than PMOS → logic tends to pull down quickly         |
| **SF** | Slow    | Fast    | **Slow-Fast Corner** | PMOS faster than NMOS → logic tends to pull up quickly           |


| Corner | Mobility (μ)         | Vth     | Delay            | Power    | Use Case            |
| :----- | :------------------- | :------ | :--------------- | :------- | :------------------ |
| **TT** | nominal              | nominal | nominal          | nominal  | Normal operation    |
| **SS** | low                  | high    | slowest          | lowest   | Worst-case timing   |
| **FF** | high                 | low     | fastest          | highest  | Best-case timing    |
| **SF** | NMOS slow, PMOS fast | –       | pull-up faster   | moderate | Rise/fall skew test |
| **FS** | NMOS fast, PMOS slow | –       | pull-down faster | moderate | Rise/fall skew test |



**DAY 1: Netlist file**

```
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description



XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.65 l=0.25

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

While including the library " .lib "sky130_fd_pr/models/sky130.lib.spice" **tt** " we can give what evrr process corner is required.

**Invoke SPICE Using:**

```

ngspice file_name.spice

```

**For plotting:**

<img width="1363" height="654" alt="Screenshot from 2025-10-16 10-13-31" src="https://github.com/user-attachments/assets/9bdb57ce-897d-44d3-ab9e-9e01d8151c42" />

**Plot:**

<img width="1363" height="654" alt="Screenshot from 2025-10-16 10-13-23" src="https://github.com/user-attachments/assets/e82f6167-b6ce-49f2-b539-35d12580cf6a" />

