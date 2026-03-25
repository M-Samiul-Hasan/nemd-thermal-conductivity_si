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

## Method Summary

1. Build crystalline Si using a diamond lattice
2. Minimize the initial structure
3. Initialize atomic velocities at 300 K
4. Equilibrate the system using NPT
5. Switch to NVE for the transport stage
6. Define hot and cold slabs along the z-direction
7. Apply Langevin thermostats to the slabs
8. Measure the temperature profile with `fix ave/chunk`
9. Save thermostat energy tallies to `thermo.csv`
10. Fit the temperature gradient and heat input rate in Python
11. Calculate thermal conductivity using Fourier's law