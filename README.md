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

| ID | Benchmark | System | Method | Main point |
| --- | --- | --- | --- | --- |
| 001 | [Porphin core scaling](benchmarks/001-porphin-core-scaling/) | Porphin, 38 atoms | B3LYP/def2-SVP | TDDFT/TDA and geometry-optimization scaling on the same machine. |
| 002 | [FeCN6 N K-edge basis comparison](benchmarks/002-fecn6-nkxas-basis-comparison/) | `[Fe(CN)6]4-`, 13 atoms | TDDFT/TDA, def2-TZVP vs aug-cc-pVTZ on N | Augmenting only the N basis improves PBE0 and CAM-B3LYP; BP86 (no exact exchange) stays poor. |

## Repository Policy

The `.out` files are kept because they contain the exact ORCA input block,
software version, timings, and calculation details. Heavy restart/scratch files
such as `.gbw`, `.cis`, `.densities`, and related artifacts are intentionally
ignored.
