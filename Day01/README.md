## MOSFET Behavior

A MOSFET (Metal–Oxide–Semiconductor Field-Effect Transistor) is a voltage-controlled device used to control current flow between the drain and source terminals. The voltage applied to the gate terminal (Vgs) determines how much current (Id) flows through the channel. When Vgs is below a certain threshold voltage (Vth), the MOSFET remains OFF, and no channel exists between drain and source. Once Vgs exceeds Vth, an inversion layer (conductive channel) forms, allowing current to flow. The MOSFET can thus act as a variable resistor or as a current source, depending on the region of operation.

## Regions of Operation

**Cutoff Region**
When Vgs < Vth, the MOSFET is OFF. There is no conduction channel between drain and source, and the drain current (Id) is approximately zero. This region is used for switching applications when the transistor is meant to block current.

**Linear (Triode) Region**
When Vgs > Vth and Vds is small, the MOSFET behaves like a voltage-controlled resistor. The drain current increases linearly with Vds. The relationship can be approximated as:
Id = k[(Vgs – Vth)Vds – (Vds²/2)],
where k is a device constant. This region is used in analog circuits like amplifiers.

**Saturation (Active) Region**
When Vds ≥ (Vgs – Vth), the channel near the drain becomes pinched off, and the current becomes independent of Vds. The MOSFET now acts as a constant current source, and the drain current is given by:
Id = (1/2)k(Vgs – Vth)².
This region is widely used in analog and digital circuits for amplification.

## ID vs. VDS Characteristics

The Id–Vds characteristics graph shows how the drain current changes with the drain-to-source voltage for different gate voltages (Vgs):

-  For Vgs < Vth, Id remains nearly zero (cutoff region).
-  As Vgs increases beyond Vth, the Id–Vds curve starts from the origin and rises linearly at first (linear region).
-  With further increase in Vds, the curve gradually flattens, indicating saturation, where Id becomes nearly constant regardless of further Vds increase.


## Threshold Voltage Extraction

**Threshold voltage (Vt)** is the minimum gate-to-source voltage (Vgs) at which a MOSFET begins to strongly conduct. Accurate Vt extraction is vital for device characterization, quality control, and modeling in circuit design. Two common methods are used to extract Vt based on measured data.

### 1. Sweep (Vgs) vs. Id – The Measurement

To analyze MOSFET behavior, a "sweep" is performed where the gate-source voltage (Vgs) is gradually increased, and the corresponding drain current (Id) is measured. This generates an Id-Vgs curve, which provides information about when the MOSFET turns on and how it behaves in different operating regions.

### 2. Extracting Threshold Voltage (Vt) by Linear Extrapolation

In the **linear extrapolation method**, the Id-Vgs data (often plotted with Id on a logarithmic scale) is analyzed near the region where current just begins to rise significantly. A straight line is fit to the linear portion of the Id-Vgs curve, usually in the region of maximum transconductance (gm). The point where this line intercepts the Vgs (x) axis is taken as the threshold voltage, Vt. This method is popular because it minimizes errors from source/drain resistance but can be affected by mobility degradation in short-channel devices.

### 3. Velocity Saturation

**Velocity saturation** refers to the phenomenon in short-channel MOSFETs where, beyond a certain electric field, the carrier velocity no longer increases linearly with increasing field but instead approaches a maximum limit. This affects the Id-Vds and Id-Vgs characteristics, especially at high drain voltages. In modern and small-geometry MOSFETs, velocity saturation means the current increases more slowly with higher Vgs than what the classic quadratic model predicts.

---

In summary:
- Sweeping Vgs and measuring Id reveals the device's turn-on behavior.
- Linear extrapolation of the Id-Vgs curve estimates Vt where conduction just begins.
- Velocity saturation must be considered in modern devices, as it influences the accuracy of extraction methods and device modeling.


## CMOS Inverter: Voltage Transfer Characteristics

A **CMOS inverter** is a fundamental digital logic circuit made from a complementary pair of MOSFETs: one NMOS and one PMOS transistor, connected in series between the supply voltage (VDD) and ground. When the input voltage (Vin) is high, the NMOS turns on and the PMOS turns off, pulling the output low; when Vin is low, the NMOS is off and the PMOS is on, pulling the output high. Thus, the circuit inverts the logic level of the input.

### Voltage Transfer Characteristic (VTC)

The **Voltage Transfer Characteristic (VTC)** of a CMOS inverter is a plot of output voltage (Vout) versus input voltage (Vin). This curve provides key information on how the inverter transitions between logic states as the input changes. The VTC typically has a steep transition region, resembling an inverted step function, which ensures that the inverter switches quickly and reliably between high and low output states.

The ideal VTC can be divided into three main regions:

- **Region 1 (Vin ≈ 0):** The input is low; NMOS is off, PMOS is on. Vout is pulled up close to VDD (logic high).
- **Region 2 (Vin ≈ VDD):** The input is high; NMOS is on, PMOS is off. Vout is pulled down close to ground (logic low).
- **Region 3 (Transition/Midpoint):** Both transistors operate in their active regions. As Vin increases through this zone, Vout rapidly decreases from high to low. The point where Vin = Vout is called the switching threshold and is crucial for determining noise margins and signal integrity.

### Noise Margins and Switching Thresholds

The steepness and position of the transition region in the VTC determine the inverter's **noise margins**, which indicate how much unwanted voltage variation (noise) can be tolerated without causing a logic error. Good noise margins and a transition centered near half the supply voltage ensure robust operation in the presence of noise.

### Impact of Transistor Sizing

Transistor sizing affects the shape and position of the VTC. A stronger PMOS (wider channel) increases the output's ability to pull high, shifting the transition region to higher Vin, and vice versa for a stronger NMOS. Proper sizing ensures a symmetric transition and balanced rise/fall times, optimizing noise immunity and performance.

In summary, the voltage transfer characteristic of a CMOS inverter is central to understanding its performance, noise immunity, and switching behavior in digital circuits.

## Transient Behavior: Rise and Fall Delays

**Rise time** is defined as the time interval during which the output voltage of a CMOS inverter transitions from 10% to 90% of its final high level. Conversely, **fall time** refers to the time taken for the output to transition from 90% down to 10% of its high level. These times represent how quickly the inverter output can charge or discharge the load capacitance.

The propagation delay, often split into **tₚLH** for low-to-high transitions and **tₚHL** for high-to-low transitions, is the time difference between when the input crosses its midpoint and when the output crosses its midpoint voltage level. It quantifies how fast the inverter responds to input changes.

This delay and rise/fall times can be modeled using a simple RC circuit analogy, where the transistor’s on-resistance and the load capacitance form an RC network. The time constant \( \tau = RC \) determines the charge and discharge rates of the output node, and hence directly influences the switching speed. The propagation delay can be approximated as \( t_p = 0.69RC \).

Several factors influence rise and fall delays:

- **Transistor properties:** The ON resistance of the PMOS and NMOS transistors affects charging and discharging speeds; NMOS transistors typically have higher mobility, causing fall times to usually be shorter than rise times.
- **Load capacitance:** Larger capacitive loads require more time to charge or discharge, increasing delays.
- **Parasitic capacitances and resistances:** Internal device capacitances and resistances add to delay.
- **Supply voltage and temperature:** Variations in supply voltage and temperature can speed up or slow down switching.

In practical CMOS inverters, delays form the rising and falling edges of output signals. Designers characterize these delays carefully because they affect the maximum speed and power consumption of digital circuits.

