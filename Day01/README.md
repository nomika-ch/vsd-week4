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
