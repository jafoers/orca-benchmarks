# ORCA Benchmarks

Small, reproducible ORCA benchmark case studies. Each benchmark folder is meant
to be readable on its own: geometry, ORCA output files, one lightweight plot, and
a short README with the relevant hardware and method details.

## Hardware

Unless noted otherwise, benchmarks were run on a single dual-socket workstation:

- CPU: 2x Intel Xeon E5-2696 v4
- Physical cores: 44
- Hardware threads: 88
- RAM: 121 GiB
- ORCA: 6.1.1

## Benchmarks

| ID | Benchmark | System | Method | Result |
| --- | --- | --- | --- | --- |
| 001 | [Porphin core scaling](benchmarks/001-porphin-core-scaling/) | Porphin, 38 atoms | B3LYP/def2-SVP | TDDFT/TDA and geometry-optimization scaling on the same machine. |
| 002 | [FeCN6 N K-edge basis comparison](benchmarks/002-fecn6-nkxas-basis-comparison/) | `[Fe(CN)6]4-`, 13 atoms | TDDFT/TDA, def2-TZVP vs aug-cc-pVTZ on N | Augmenting only the N basis improves PBE0 and CAM-B3LYP; BP86 stays poor. |
| 003 | [ZnTPP CPCM TDA comparison](benchmarks/003-zntpp-cpcm-tda-comparison/) | ZnTPP, 77 atoms | TDDFT, def2-TZVP, CPCM(toluene) | TDA-on vs full TD-DFT for five representative functionals against the toluene UV-vis spectrum. |
| 004 | [NiTPP, PdTPP, PtTPP B-band trend](benchmarks/004-ni-pd-pt-tpp-bband-trend/) | NiTPP, PdTPP, PtTPP, 77 atoms each | Full TD-DFT, def2-TZVP, CPCM(toluene) | The B band blue-shifts monotonically from Ni to Pd to Pt across the five-functional sweep. |
| 005 | [B-band TDA vs full TD-DFT shift across metals](benchmarks/005-metal-porphyrin-bband-tda-deltas/) | MgTPP, ZnTPP, CdTPP, NiTPP, PdTPP, PtTPP, 77 atoms each | TDDFT/TDA vs full TD-DFT, def2-TZVP, CPCM(toluene) | TDA blue-shifts the B band for every metal and functional, with smaller shifts for NiTPP, PdTPP, and PtTPP than for MgTPP, ZnTPP, and CdTPP. |
| 006 | [Porphyrinoid core ladder](benchmarks/006-porphyrinoid-core-ladder/) | Porphin, chlorin, bacteriochlorin | Full TD-DFT, def2-TZVP, CPCM(CH2Cl2) | Across five functionals, the free-base core ladder red-shifts monotonically from porphin to bacteriochlorin. |
| 007 | [Mg core ladder shifts](benchmarks/007-mg-core-ladder-shifts/) | Mg-porphin, Mg-chlorin, Mg-bacteriochlorin | Full TD-DFT, def2-TZVP, gas phase and CPCM(CH2Cl2) | Mg insertion blue-shifts porphin and chlorin, but red-shifts bacteriochlorin. |
| 008 | [Mg-bacteriochlorin axial ligation](benchmarks/008-mgbacteriochlorin-axial-ligation/) | Mg-bacteriochlorin with H2O, MeOH, imidazole | Full TD-DFT, def2-TZVP, CPCM(CH2Cl2) | H2O and MeOH are nearly identical; imidazole slightly blue-shifts Qx and the B-band pair while leaving Qy almost unchanged. |
| 009 | [Mg-chlorin axial ligation](benchmarks/009-mgchlorin-axial-ligation/) | Mg-chlorin with H2O, MeOH, imidazole | Full TD-DFT, def2-TZVP, CPCM(CH2Cl2) | H2O and MeOH are nearly identical; imidazole lowers S1, S2, and both bright B-region states. |

## Repository Policy

The `.out` files are kept because they contain the exact ORCA input block,
software version, timings, and calculation details. Heavy restart/scratch files
such as `.gbw`, `.cis`, `.densities`, and related artifacts are intentionally
ignored.
