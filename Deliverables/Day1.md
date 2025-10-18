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
