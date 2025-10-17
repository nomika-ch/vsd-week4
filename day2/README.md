# Why we need SPICE (e.g., ngspice)

SPICE stands for Simulation Program with Integrated Circuit Emphasis.
It’s a circuit simulator used to analyze and verify electronic circuits before physically building them.

**Main Purpose**

SPICE helps us understand how a circuit behaves electrically — in terms of voltages, currents, power, and timing — without using real hardware.

It answers questions like:
-  Will my amplifier actually amplify the input correctly?
-  Does the MOSFET switch on at the expected gate voltage?
-  What is the delay between input and output in a logic gate?
-  Will the circuit oscillate or become unstable?

Why we simulate instead of directly building?
| Without SPICE                            | With SPICE (e.g., ngspice)            |
| ---------------------------------------- | ------------------------------------- |
| Need to **physically build** the circuit | Just **write a netlist** and simulate |
| Mistakes can **damage components**       | Safe and reversible                   |
| Hard to measure internal node voltages   | SPICE gives **access to every node**  |
| Expensive for large ICs                  | **Free & scalable** simulation        |
| Takes time to test many designs          | Can **sweep parameters** quickly      |


**What SPICE can do**

DC Analysis – finds steady-state voltages/currents.
→ e.g., What is 𝑉𝑜𝑢𝑡 for a given 𝑉𝑖𝑛​?

AC Analysis – frequency response of circuits.
→ e.g., Gain vs frequency for an amplifier.

Transient Analysis – behavior over time.
→ e.g., Output waveform of a CMOS inverter switching.

→ Noise, Monte Carlo, and Temperature Analysis – advanced checks for reliability and variability.

**Why ngspice specifically?**

-  It’s an open-source version of SPICE (developed from Berkeley SPICE).
-  Works on Linux, Windows, and macOS.
-  Can simulate analog, digital, and mixed-signal circuits.
-  Supports Verilog-A and BSIM models for realistic MOSFETs.
-  Used in VLSI and EDA tools (e.g., used in SkyWater 130nm PDK simulations).

**Example**

```

* CMOS Inverter using SkyWater 130nm PDK
.include /path/to/sky130_fd_pr/models/sky130.lib.spice TT
Vin in 0 PULSE(0 1.8 0ns 1ns 1ns 10ns 20ns)
Mp out in vdd vdd pmos W=1u L=0.18u
Mn out in 0   0   nmos W=0.5u L=0.18u
Vdd vdd 0 1.8
.tran 1ns 40ns
.end

```

Running this in ngspice gives us the output waveform showing how Vout switches with Vin, confirming if it meets logic thresholds and delay targets.

SPICE (like ngspice) is the bridge between theoretical circuit design and real-world hardware — letting you verify performance, correctness, and robustness before fabrication.

**Code explanation**
Vin in 0 PULSE(0 1.8 0ns 1ns 1ns 10ns 20ns)

-  This defines the input voltage source (Vin).
-  in → positive terminal node name (input node).
-  0 → negative terminal (ground).
-  PULSE(...) → creates a square wave (digital-like) signal.

The pulse parameters inside the parentheses are:

1. PULSE(V1 V2 TD TR TF PW PER)

| Parameter | Meaning                     | Value |
| --------- | --------------------------- | ----- |
| **V1**    | Initial (low) voltage       | 0 V   |
| **V2**    | High voltage                | 1.8 V |
| **TD**    | Delay before starting pulse | 0 ns  |
| **TR**    | Rise time                   | 1 ns  |
| **TF**    | Fall time                   | 1 ns  |
| **PW**    | Pulse width (time high)     | 10 ns |
| **PER**   | Period (total cycle time)   | 20 ns |

So this creates a square wave that toggles between 0 V and 1.8 V every 20 ns —  digital input signal.

2. Mp out in vdd vdd pmos W=1u L=0.18u

This defines the PMOS transistor (name = Mp).

| Parameter        | Description                                      |
| ---------------- | ------------------------------------------------ |
| **out**          | Drain node → output of inverter                  |
| **in**           | Gate node → input signal                         |
| **vdd**          | Source node → connected to VDD (1.8 V)           |
| **vdd**          | Bulk (body) → tied to VDD for PMOS               |
| **pmos**         | Model name (you must define or include from PDK) |
| **W=1u L=0.18u** | Channel width = 1 µm, length = 0.18 µm           |

This PMOS pulls the output high (1.8 V) when the input is low (0 V).

3. Mn out in 0 0 nmos W=0.5u L=0.18u

This defines the NMOS transistor (name = Mn).

| Parameter          | Description                           |
| ------------------ | ------------------------------------- |
| **out**            | Drain → connected to output           |
| **in**             | Gate → connected to input             |
| **0**              | Source → connected to ground          |
| **0**              | Bulk → connected to ground            |
| **nmos**           | Model name                            |
| **W=0.5u L=0.18u** | NMOS width = 0.5 µm, length = 0.18 µm |

This NMOS pulls the output low (0 V) when input is high (1.8 V).

4. Vdd vdd 0 1.8

This defines the DC supply voltage source.

| Node 1 | Node 2 | Voltage |
| ------ | ------ | ------- |
| vdd    | 0      | 1.8 V   |

Provides the power supply for the inverter.

5. .tran 1ns 40ns

This is a transient analysis command — simulates the circuit over time.

Syntax: .tran <tstep> <tstop>

| Parameter | Meaning                    |
| --------- | -------------------------- |
| **1ns**   | Time step for storing data |
| **40ns**  | Total simulation time      |

It runs a time-domain simulation for 40 ns and gives waveforms for Vin, Vout, etc.

6. .end

Marks the end of the SPICE netlist.
No statements after this line will be processed.

7. .include /path/to/sky130_fd_pr/models/sky130.lib.spice TT

This line loads the transistor models from the SkyWater 130nm PDK.

Replace **/path/to/** with the actual path where the PDK is installed. TT stands for Typical-Typical corner — normal process, voltage, and temperature.

This file contains:

NMOS model → sky130_fd_pr__nfet_01v8

PMOS model → sky130_fd_pr__pfet_01v8

Other device parameters (threshold voltage, capacitance, etc.)
