# Crystalline Si Thermal Conductivity by Direct NEMD in LAMMPS

This repository contains a beginner-friendly direct nonequilibrium molecular dynamics (NEMD) workflow for estimating the thermal conductivity of crystalline silicon using LAMMPS and Python.

## Overview

The simulation uses:

- diamond-cubic silicon
- Stillinger–Weber (SW) potential
- direct NEMD with hot and cold slabs
- slab-averaged temperature profile
- thermostat energy tallies to compute heat flux
- Python post-processing to estimate thermal conductivity

The purpose of this repository is to document a clean learning workflow for MD-based thermal transport simulation.

# Method

## Simulation type
Direct nonequilibrium molecular dynamics (direct NEMD)

## Material
Crystalline silicon (diamond cubic)

## Potential
Stillinger–Weber (SW)

## Workflow
- Build the simulation cell
- Minimize the structure
- Initialize velocities at 300 K
- Equilibrate using NPT
- Switch to NVE
- Define hot and cold slabs
- Apply Langevin thermostats to hot/cold slabs
- Measure slab temperature profile along z
- Save cumulative thermostat energies
- Post-process in Python to calculate thermal conductivity

## Thermal conductivity calculation

The thermal conductivity is computed from Fourier's law:

k = J / |dT/dz|

where:
- J is the heat flux
- dT/dz is the fitted temperature gradient

The heat flux is obtained from the slope of cumulative thermostat energy vs time.
Because periodic boundaries create two heat-flow directions, the heat-flux expression includes a factor of 2.
