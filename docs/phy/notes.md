# Notes

## Definitions:

**System**: a region w en/matter separated from the surr. by *arbitrarily* imposed wall of boundary
**Boundary**: an *arbitrary* *closed* surface through which en/mass enter/leave the sys
**Surrounding**: anything that interacts w the sys

**props**: things that describe the sys. temp, pressure, vol, etc.

**Closed** sys: no transfer of en across the boundary
**Open** sys: transfer of en across the boundary

**Heat**: En transfer due to temp diff only. higher -> lower

## First law of TD: Conservation of Energy
Energy can be transformed from 1 form to another, but can neither be created nor destroyed

**Energy: state function**

$\Delta E_{sys} = (\sum E_{sys,2} - \sum E_{sys,1})$

This holds for first der. wrt time.

$\dot{E}_{sys} = \Delta \dot{Q} + \Delta \dot{W} + \Delta \dot{E}_{flow}$

Energy can be transfered in the form of heat (flow of heat), in the form of work done (power) and in the form of mass (energy $\dot{E_{flow}}$ )

for a closed sys, $\dot{E}_{sys} = \dot{U}_{sys} = \Delta \dot{Q} + \Delta \dot{W}$

## Heat Transfer

Bodies do not contain heat, its only id-ed as it passes across the sys bounds

### Modes of Heat Transfer

#### Conduction
By intermol. interactions

Fourier's Law: $\dot{Q} =  -\kappa A \frac{dT}{dx}$

$\kappa$ - therm conduct.

#### Convection
By diffusion n bulk movement of fluid. Occurs b/n surfaces

Newton's Law of cooling: $\dot{Q} = h A (T_h - T_c)$

h - heat transfer coeff.

1. Forced: due to pump/fan/external cause. ex: fan over PCB
2. Free: Naturally due to buoyncy effects and differences in density. ex: air in contact w hot things

#### Radiation
By EM rad. No medium req. Dominant method of heat transfer for temp > 400°C

Stefan-Boltzman Law: $\dot{Q} = \epsilon \sigma A (T_h^4 - T_c^4)$

$\epsilon$ - emissivity $(0 < \epsilon < 1)$

$\sigma$ - Stefan-Boltzman Const $(5.67 \times 10^{-8})$

### Steady and Transient state

Steady state: in = out. $\dot{Q}_{conv} = \dot{Q}_{cond} = \dot{Q}_{rad}$

### Work
Work is power out/in

## Electrical Analog for Conduction and Convection

$\dot{Q}_{cond} =  -\kappa A \frac{dT}{dx} = \cfrac{T_2-T_1}{\cfrac{L}{\kappa A}} = \cfrac{\Delta T}{R_{cond}}$

$\dot{Q}_{conv} = h A (T_h - T_c) = \cfrac{T_2-T_1}{\cfrac{1}{h A}} = \cfrac{\Delta T}{R_{conv}}$

Thus,

$R_{cond} = \cfrac{L}{\kappa A}$

$R_{conv} = \cfrac{1}{h A}$

Here, $T$ is analogous to $V$ and $Q$ is analogous to $I$. A similar analysis can be done to compare series and parallel heat flow!

## Conservation of Mass & Energy

Definition of boundaries are important for system. Include them in your answers

### Conservation of Mass

Mass can neither be created nor destroyed

### Mass flow rate

Control Volume

$\cfrac{dm_{cv}}{dt} = \cfrac{dm_{sys}}{dt} = in - out$

This change is 0 in `Steady State`

### Conservation of Energy

Energy can neither be created nor destroyed but it can be transformed from one form to another

### Flow Work

$\dot{W}_i = P_i \dot{m}_i v_i$ - in

$\dot{W}_e = P_e \dot{m}_e v_e$ - out (effluent?)

P - Pressure, m - mass flow rate, v = 1/density (specific volume, volume of 1 kg of mat)

$u_{internal} = PE + KE$ ,

$h = u_{internal} + Pv$

$\dot{E}_{flow, in} - \dot{E}_{flow, out} = \dot{m}_{in} h_{in} + \dot{m}_{in} g z_{in} + \frac{1}{2}\dot{m}_{in} v^2_{in} - (\dot{m}_{out} h_{out} + \dot{m}_{out} g z_{out} + \frac{1}{2}\dot{m}_{out} v^2_{out})$

## Entropy

$\Delta S = \cfrac{\delta Q}{T}$

$\cfrac{dS_{sys}}{dt} = \sum\cfrac{\dot{Q}_{in, j}}{T_j} - \sum\cfrac{\dot{Q}_{out, j}}{T_j} + \sum \dot{m}_i s_i - \sum \dot{m}_e s_e + \dot{\sigma}_{gen, cv}$

s - specific entropy

$\dot{\sigma}_{gen, cv} \geq 0$ Always

When reading the entropy values from table, if the pressure is not 1 Bar, you need to correct for the term:

$s_2 - s_1 = s^{\circ}_2 - s^{\circ}_1 - rln\cfrac{P_2}{P_1}$

r = gas constant, $\cfrac{R}{M_w}$

$R = 8.314 J/mol.K$

### Efficiency

$\eta = \cfrac{W_{out}}{Q_h} = \cfrac{Q_h - Q_c}{Q_h}$

$\eta_{carnot} = 1 - \cfrac{T_C}{T_H}$

$COP_{ref} = \cfrac{Q_c}{W_{in}} = \cfrac{Q_c}{Q_h - Q_c} = \cfrac{T_c}{T_h - T_c}$

$COP_{heat} = \cfrac{Q_h}{W_{in}} = \cfrac{Q_h}{Q_h - Q_c} = \cfrac{T_h}{T_h - T_c}$


## Exergy

A sys delivers the max possible work if it goes through a rev. process from initial to final (dead) state.

Dead State => in thermodynamic equilibrium with its surroundings. Repr by subscript 0

**Exergy is defined as the maximum possible work which represents useful work potential of the system at a specific state**

### Irreversibility and Reversible work

$I = W_{rev, out} - W_{out}$

$I = W_{in} - W_{rev, in}$

Irrevrsibility is equivalent to exergy destroyed as it is viewed as wasted work potential or lost opportunity to do work

Reversible work is the maximum amount of useful work that can be produced as a system undergoes a process between the specific initial and final states

if $\dot{\sigma}_{gen} = 0$ then all work is reversible

$\eta_{carnot} = \eta_{rev} = \cfrac{W_{rev,out}}{Q_h}$

### Exergy for fixed mass system

$X = U-U_0 + P_0(V-V_0) - T_0(S-S_0) + \cfrac{mv^2}{2} + mgz$

specific exergy:

$\phi = u-u_0 + P_0(v-v_0) - T_0(s-s_0) + \cfrac{v^2}{2} + gz$

$X_2 - X_1 = U_2-U_1 + P_0(V_2-V_1) - T_0(S_2-S_1) + \cfrac{m(v_2^2 - v_1^2)}{2} + mg(z_2-z_1)$

### Exergy Transfer Accompanying Work

$X = W = nRT.ln(\cfrac{V_2}{V_1})$

### Exergy Transfer Accompanying Heat

$X = \dot{W} = \eta_{carnot}\dot{Q} = (1 - \cfrac{T_0}{T})\dot{Q}$

$\dot{X} = \dot{X}_{in} - \dot{X}_{out} - \dot{X}_{destroyed}$

$\dot{X}_{in} = \dot{X}_{heat, in} + \dot{X}_{work, in}$

$\dot{X}_{out} = \dot{X}_{heat, out} + \dot{X}_{work, out}$

$I = X_{destroyed} = W_{lost} = T_0 \sigma_{gen}$

### Second Law (Exergetic Efficiency)

$\epsilon = \cfrac{\eta}{\eta_{rev}} = \cfrac{COP}{COP_{rev}}$

$\epsilon = \cfrac{W_{out}}{W_{rev, out}} = \cfrac{W_{rev, in}}{W_{in}}$

left one => power producing devices, right one => power consuming devices

$\epsilon = \cfrac{\text{exergy recovered}}{\text{exergy supplied}} = 1 - \cfrac{\text{exergy destroyed}}{\text{exergy supplied}}$

$\text{exergy recovered} = \dot{m}_{in}{\psi_{in}} - \dot{m}_{out}{\psi_{out}}$

$\text{exergy supplied} = \dot{X}_{in}$

### Exergy Flow in an Open Sys.

Specific exergy:

$\psi = (u - u_0) + (Pv - P_0 v_0) - T_0(s - s_0) + \cfrac{v^2}{2} + gz$

$h = u + Pv$

$\psi = (h - h_0) - T_0(s - s_0) + \cfrac{v^2}{2} + gz$

$\cfrac{dX_{sys}}{dt} = \dot{X}_{heat, in} - \dot{X}_{heat, out} + \dot{X}_{work, in} - \dot{X}_{work, out} + \sum \dot{m_{in}}\psi_{in} - \sum \dot{m_{out}}\psi_{out}$

## Batteries

### Important Battery Parameters to Consider

1. Cell Voltage $E^{\circ}_{cell}$
2. Energy Density/Specific Energy
3. Capacity

Not in focus

1. Power Density/Specific Power
2. Self‐discharge rate/charging cycles
3. Charge‐Discharge rate life time
4. Capital/Operating cost

### Specific Energy
Energy stored per unit mass of battery (specific energy)

$e = \cfrac{V.n.q}{m}$

Energy stored per unit volume of battery (energy density)

$e = \cfrac{V.n.q}{v}$

$V$ - Voltage, $n$ - num of electrons, $q$ - charge on one electron, $m$ - mass of active materials, $v$ - volume of active materials

### Current
C-rate - The rate of time in which it takes to charge or discharge
This is the value of current in amperes that is numerically equal to the batter's capacity in Ampere hours

### Voltage
emf is different for different currents drawn. Higher current => lesser voltage. This is because more active mass is used => the potential difference between the cathode and anode is reduced fast

$E_{cell} = E^{\circ}_{cell} - \cfrac{RT}{nF}ln(Q)$

Q - Reaction Quotient

$F = N_a \times e = 96500 C$

charge on one mole of electrons, Faraday's constant

Nominal Voltage - (midpt voltage) Voltage when the battery is at 1/2 capacity

### Capacity
$\text{Capacity} = \text{Current} \times \text{Time}$

Look at the discharge characterisitics from week 6 cohort 2

### Self Discharge rate

Self‐discharge ‐ loss of capacity through reactions during the battery storage and when battery is not connected to a load

These reactions are mainly caused by thermodynamic instabilities between active masses and cell components, resulting in consumption of active masses

Capacity decreases over time as a result of loss through self‐discharge

Self‐discharge is usually reversible ‐ battery is recharged the capacity is restored

For lead–acid batteries the product of discharge reaction is lead sulfate which may build and grow irreversibly if the recharge doesn’t occur in a certain time – a battery if left for a long period of time without recharging, the available capacity will be reduced

### Applications of Batteries

1. Electromotibility
2. Standalone PV sys
3. Mobile Application
4. Backup/stationary batteries

### Different Types of PV Systems

Grid Tie - on roof
Grid Tie - with backup batteries
Off Grid - Standalone

### Different Components in a Standalone PV System

1. Solar Panel - Source
2. Energy Storage - Batteries
3. Solar Charge Controller - Manages the charging of the battery and operation of the load. It ensures charging voltage and current are well controlled to protect the lifespan of the battery used.
4. Load

Steps to design a standalone system:

1. Determine the load energy requirement
2. Determin the Size of the battery
3. Determin the Size of the PV sys

#### Depth of Discharge

$DOD = \cfrac{\text{capacity that is discharged from a fully charged battery}}{\text{battery nominal capacity}}$

#### End of Life

1. Batteries that have reached the end of their usefulness and/or lifespan and no longer operate at sufficient capacity
2. Percent of capacity at EoL of battery is usually defined as 80% of original capacity
3. It may be lower in other applications

#### Days of Autonomy
The number of days that the battery can supply the site’s loads without any support from generation sources

1. For a standalone PV system, it requires some battery reserve to ensure reliability of service and to provide time for intervention in the event of an unanticipated occurrence (e.g. poor weather or failure of a system component)
2. The number of days of autonomy is a system design requirement that takes the following into consideration:

    1. System application – critical load applications require more autonomy than non‐critical applications
    2. System availability – minimum percentage of the time that the PV system should be able to satisfy
    the system’s specified design loads
    3. Solar irradiance variability – daily and seasonal variations in solar irradiance affect the required
    autonomy
    4. Predictability of load – load may not be predictable or the load may be adjusted such as when
    dropping nonessential loads
    5. Recharge capability – battery may not be fully recharged between discharges if the array is
    insufficiently sized or the recharge time is too short
    6. Accessibility of site – worse‐case time required to reach the site and to correct for any problem

#### Number of batteries

#### Size of solar Panel

1. Using load requirement/avg daily irradiance for the area of the solar panel
2. Simulation

### Materials and manufacturing issues of Li-Ion batteries

1. Electron transport in solid
2. Ionic diffusion in liquid and solid
3. Structre/Volume change: strain
4. Solid Electrolyte Interphase
5. Saftey Control

### Irradiance/Intensity ($W/m^2$)

$I = \cfrac{\partial P}{\partial A}$

$1 kW/m^2 = 1 \; Sun$ is the standard $I_{rad}$ used to test solar cells.

### Spectral Irradiance ($W/m^2.nm$)

$S(\lambda) = \cfrac{\partial I}{\partial \lambda} = \cfrac{\partial^2 P}{\partial \lambda \partial A}$

$I_{rad} = \int\limits_{\lambda_1}^{\lambda_2} S(\lambda) d\lambda$

### Formation of Electron Hole Pairs

Typical Energy band diagrams

1. Metals: Half filled conduction band (no band gap/overlapping conduction and valence band) ($Au$, $Cu$, $Al$, $Ag$)
2. Semi Conductors: bad gap $< 5 \; eV$ ($Si$, $Ge$, $GaAs$, $BiTe$, $ZnSe$)
2. Insulators: bad gap $> 5 \; eV$ ($SiO_2$)

Generation: A photon with energy $E = hf > E_{bg}$ can knock off electrons from the valence band and excite them up to the conduction band. An electron hole pair is formed.

Recombination: If not "used", the electron will fall back to the valance band, releasing energy in the form of light or heat

Enter $n$ and $p$ type doping. When $n$ and $p$ doped sc are put next to each other, A region called the depletion region is created. It creates an $E$ field that drives the flow of electrons and holes

A PN junction diode allows the flow of current easily in one direction (Forward Bias) but resists the flow of current in the opposite direction (Reverse Bias)

$I_D = I_o(e^{\cfrac{eV}{k_B T}} - 1)$

The diode current is opposite in direction to the photocurrent from a solar cell ($I_{sc}$ (short circuit current))

$I = I_o(e^{\cfrac{eV}{k_B T}} - 1) - I_{sc}$

$I_o$: Reverse saturation current. Due to diffusive flow of minority electrons from the p side to the n side and the minority holes from the n to p side. Unaffected by rev bias but sensitive to temp changes

When the solar panel is in operation, $I_{sc} > I_o(e^{\cfrac{eV}{k_B T}} - 1)$ and the current is produced from the p terminal.

The IV plot for a solar panel is usually flipped and the equation is as follows:

$I_r = I_{sc} - I_o(e^{\cfrac{eV}{k_B T}} - 1)$

If the solar panel is not connected, $I_r = 0$

$I_{sc} = I_o(e^{\cfrac{eV}{k_B T}} - 1)$

$V_{oc} = \cfrac{K_B T}{e} ln\left(\cfrac{I_{sc}}{I_o} + 1\right)$

$I_o$ is a function of $T$ which grows much faster than the $T$ in the numerator. $V_{oc}$ decreases with increase in $T$

The output power of a solar cell is $IV$ determined experimentially by varying the resistive load.

$P_{max} = I_{max} V_{max} = FF I_{sc} V{oc}$

$FF = \cfrac{P_{max}}{I_{sc} V_{oc}}$

$FF$ - Fill Factor

$\eta = \cfrac{P_{out}}{P_{in}} = FF \cfrac{I_{sc} V_{oc}}{P_{in}}$
