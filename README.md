# Supplementary Material: Detailed Mathematical Derivations

**Paper Title:** Modeling primary frequency regulation of thermal units considering boiler thermal inertia and thermal hysteresis
**Authors:** Pengfei Qi

---

## Overview

This repository contains the supplementary mathematical formulations and detailed parameter derivations for the paper mentioned above. Due to space limitations in the conference proceedings, the full set of differential algebraic equations (DAEs) describing the non-equilibrium thermodynamics of the drum, the hydrodynamics of the circulation loop, and the distributed heat transfer mechanism are presented here.

## 1. Drum Non-Equilibrium Thermodynamic Model

To accurately capture the "false water level" and pressure response, the drum is modeled using a two-phase non-equilibrium lumped parameter model. Unlike simplified equilibrium models, separate mass and energy conservation equations are applied to the liquid and vapor phases.

### Mass Conservation

The mass balance for the liquid phase (Ml) and vapor phase (Mg) is defined as:

    d(Ml)/dt = m_eco + m_riser,l - m_dc - m_evap

Where 'm_evap' represents the phase transfer rate at the interface (evaporation or condensation).

### Energy Conservation

The energy balance equations account for the enthalpy changes in both phases:

    d(Ml * ul)/dt = m_eco * h_eco + m_riser,l * h_riser,l - m_dc * hl - m_evap * hg - Q_ls

**Variables:**
* ul, ug: Specific internal energy of saturated liquid and vapor.
* h: Specific enthalpy.
* Q_ls: Heat transfer rate at the liquid-steam interface.
* m_steam: Main steam mass flow rate.

## 2. Circulation Loop Hydrodynamics

The dynamics of the natural circulation loop are governed by the integration of the Navier-Stokes momentum equation along the closed path.

### Momentum Conservation

The circulation flow rate (m_circ) is determined by balancing the gravitational driving head against flow resistances:

    I_loop * d(m_circ)/dt = Delta_P_grav - Delta_P_fric - Delta_P_acc - Delta_P_local

**Variables:**
* I_loop: Flow inertia coefficient (Integral of 1/A dl).
* Delta_P_grav: Gravitational driving pressure head (Integral of rho * g dz).
* Delta_P_fric: Two-phase friction pressure drop (calculated using the Friedel correlation).
* Delta_P_acc: Acceleration pressure drop due to density changes.

## 3. Distributed Heat Transfer Model (Superheater & Riser)

To characterize the thermal inertia and hysteresis effects, the heating surfaces (Riser and Superheater) are discretized into N control volumes.

### Energy Balance for the i-th Control Volume

For each section 'i', we solve coupled energy equations for the metal wall and the working fluid:

**Metal Wall:**

    C_wall,i * d(Tw,i)/dt = Q_rad,i - alpha_in,i * A_in,i * (Tw,i - Tf,i)

**Working Fluid:**

    V_f,i * rho_f,i * d(hf,i)/dt = m_in,i * h_in,i - m_out,i * h_out,i + alpha_in,i * A_in,i * (Tw,i - Tf,i)

**Variables:**
* C_wall,i: Heat capacity of the tube wall for the i-th section.
* Q_rad,i: Radiant heat flux absorbed from the furnace.
* alpha_in,i: Convective heat transfer coefficient (updated dynamically).
* Tw,i, Tf,i: Temperatures of the metal wall and working fluid.
* A_in,i: Inner surface area of the tube section.

## 4. Evaluation Metrics for Frequency Regulation

The quantitative analysis of the primary frequency regulation performance relies on the Integral Energy Contribution (E_T), defined as:

    E_T = Integral[from t0 to t0+T] of (Delta_P_gen(t) dt)

Where T = 30s is the critical assessment window for the inertial response.

---

## Citation

If you use this model or data in your research, please cite our paper:

> Pengfei Qi. "Modeling primary frequency regulation of thermal units considering boiler thermal inertia and thermal hysteresis."
