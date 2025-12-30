# Supplementary-Material-Detailed-Mathematical-Derivations-and-Parameter-Settings
# Supplementary Material: Detailed Mathematical Derivations

**Paper Title:** Modeling primary frequency regulation of thermal units considering boiler thermal inertia and thermal hysteresis  
**Authors:** [Pengfei Qi]  

---

## Overview

This repository contains the supplementary mathematical formulations and detailed parameter derivations for the paper mentioned above. Due to space limitations in the conference proceedings, the full set of differential algebraic equations (DAEs) describing the non-equilibrium thermodynamics of the drum, the hydrodynamics of the circulation loop, and the distributed heat transfer mechanism are presented here.

## 1. Drum Non-Equilibrium Thermodynamic Model

To accurately capture the "false water level" and pressure response, the drum is modeled using a **two-phase non-equilibrium lumped parameter model**. Unlike simplified equilibrium models, separate mass and energy conservation equations are applied to the liquid and vapor phases.

### Mass Conservation
The mass balance for the liquid phase (MlM_l) and vapor phase (MgM_g) is defined as:

$$
\begin{aligned}
\frac{dM_l}{dt} &= m_{eco} + m_{riser,l} - m_{dc} - m_{evap} \\
\frac{dM_g}{dt} &= m_{riser,g} + m_{evap} - m_{steam}
\end{aligned}
$$

Where mevapm_{evap} represents the phase transfer rate at the interface (evaporation or condensation).

### Energy Conservation
The energy balance equations account for the enthalpy changes in both phases:

$$
\begin{aligned}
\frac{d(M_l u_l)}{dt} &= m_{eco}h_{eco} + m_{riser,l}h_{riser,l} - m_{dc}h_{l} - m_{evap}h_{g} - Q_{ls} \\
\frac{d(M_g u_g)}{dt} &= m_{riser,g}h_{riser,g} + m_{evap}h_{g} - m_{steam}h_{steam} + Q_{ls}
\end{aligned}
$$

Where:
* ul,ugu_l, u_g: Specific internal energy of saturated liquid and vapor.
* hh: Specific enthalpy.
* QlsQ_{ls}: Heat transfer rate at the liquid-steam interface.
* msteamm_{steam}: Main steam mass flow rate.

## 2. Circulation Loop Hydrodynamics

The dynamics of the natural circulation loop are governed by the integration of the Navier-Stokes momentum equation along the closed path.

### Momentum Conservation
The circulation flow rate (mcircm_{circ}) is determined by balancing the gravitational driving head against flow resistances:

$$
I_{loop} \frac{dm_{circ}}{dt} = \Delta P_{grav} - \Delta P_{fric} - \Delta P_{acc} - \Delta P_{local}
$$

Where:
* Iloop=∮1AdlI_{loop} = \oint \frac{1}{A} dl: Flow inertia coefficient.
* ΔPgrav=∮ρgdz\Delta P_{grav} = \oint \rho g dz: Gravitational driving pressure head (difference between downcomer and riser).
* ΔPfric\Delta P_{fric}: Two-phase friction pressure drop, calculated using the **Friedel correlation** for the two-phase region.
* ΔPacc\Delta P_{acc}: Acceleration pressure drop due to density changes along the heated channel.

## 3. Distributed Heat Transfer Model (Superheater & Riser)

To characterize the thermal inertia and hysteresis effects, the heating surfaces (Riser and Superheater) are discretized into NN control volumes.

### Energy Balance for the ii-th Control Volume
For each section ii, we solve coupled energy equations for the metal wall and the working fluid:

**Metal Wall:**
$$
C_{wall,i} \frac{dT_{w,i}}{dt} = Q_{rad,i} - \alpha_{in,i} A_{in,i} (T_{w,i} - T_{f,i})
$$

**Working Fluid:**
$$
V_{f,i} \rho_{f,i} \frac{dh_{f,i}}{dt} = m_{in,i} h_{in,i} - m_{out,i} h_{out,i} + \alpha_{in,i} A_{in,i} (T_{w,i} - T_{f,i})
$$

Where:
* Cwall,iC_{wall,i}: Heat capacity of the tube wall for the ii-th section.
* Qrad,iQ_{rad,i}: Radiant heat flux absorbed from the furnace.
* αin,i\alpha_{in,i}: Convective heat transfer coefficient (updated dynamically).
* Tw,i,Tf,iT_{w,i}, T_{f,i}: Temperatures of the metal wall and working fluid.
* Ain,iA_{in,i}: Inner surface area of the tube section.

## 4. Evaluation Metrics for Frequency Regulation

The quantitative analysis of the primary frequency regulation performance relies on the **Integral Energy Contribution (ETE_T)**, defined as:

$$
E_T = \int_{t_0}^{t_0+T} \Delta P_{gen}(t) dt
$$

Where T=30sT = 30s is the critical assessment window for the inertial response.

---

## Citation

If you use this model or data in your research, please cite our paper:

> [Pengfei Qi]. "Modeling primary frequency regulation of thermal units considering boiler thermal inertia and thermal hysteresis."
