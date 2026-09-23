---
layout: page
title: khem - Prebiotic Chemistry Simulator
permalink: /projects/khem/
repo_url: https://github.com/funkybooboo/khem
description: Pure-Rust simulation of 3D worlds of atoms - real elements, real bond energies, and a measured gate ladder from stability toward evolution.
---

**Repository:** [github.com/funkybooboo/khem](https://github.com/funkybooboo/khem)

khem simulates 3D worlds of atoms: ten real elements (H, C, N, O, P, S, Si,
Fe, Na, Cl) carrying real valences, masses, and electronegativities. Bonds
form and break by Boltzmann probabilities against tables of real bond
energies, steered by VSEPR geometry, while temperature, pressure, and UV
fields evolve; vents heat the seafloor, sunlight the surface. The runtime has
no concept of a cell, a genome, or reproduction: if anything alive appears,
it built itself from the rules.

You seed the world with anything buildable from atoms and bonds - a beaker of
molecules with no life in it, an RNA strand inside a lipid vesicle, a whole
cell - then let it run. Nobody knows whether evolution will take hold. That
is the experiment.

## Key Features

*   **Real chemistry, cheap dynamics:** real element properties and bond-energy tables drive phenomenological dynamics cheap enough to run billion-tick experiments on a laptop
*   **Deterministic by construction:** same seed, byte-identical run
*   **One JSON event per line:** the whole output contract - stream it, grep it, chart it, build a viewer on it
*   **A language for matter:** .kem is a hardware description language - what Verilog is to circuits, .kem is to matter; worlds compose bottom-up from element to molecule to strand to cell to world, and the standard library ships water, nucleotides, lipids, a vesicle, and a cell
*   **Measured gate ladder:** nothing is built on the substrate until it passes gates - K1 stability, K2 self-assembly, K3 replication, K4 variation, K5 selection

## Status

The engine is built and streams real output. The K1 gate ladder closed in 2D:
the thermostat, force-sanity, water-persistence, reactive-balance, and
seam-symmetry sub-gates are measured passes (the pond's 1024 waters hold
intact under bombardment, and the free-atom beaker settles to a stationary
molecule-size distribution). The 3D port landed 2026-09-08, so vesicles,
base pairs, and carbon get true geometry instead of 2D shadows - the K1
ladder now re-climbs in 3D, one gate per commit. The .kem parser stays
spec-only until the gates pass, because a language on a dead substrate is
worthless.

## Technology

Pure Rust, two crates, zero dependencies. MIT license.