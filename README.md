# STEPSS User Guide

This repository contains the LaTeX source for the **STEPSS** documentation — models reference and user guide.

## What is STEPSS?

**STEPSS** (*Static and Transient Electric Power Systems Simulation*) is an open-source power system simulation tool for dynamic studies of electrical grids. It performs power flow computations and simulates the dynamic response of power systems to disturbances under the phasor approximation.

STEPSS consists of three tightly integrated modules:

| Module | Full Name | Description |
|--------|-----------|-------------|
| **PFC** | Power Flow Computation | Determines the initial operating point using the Newton-Raphson method in polar coordinates. Computes bus voltage magnitudes and phase angles, with optional transformer ratio adjustment. |
| **RAMSES** | RApid Multiprocessor Simulation of Electric power Systems | Simulates the dynamic evolution of the power system. Supports Backward Euler, Trapezoidal, and BDF2 integration methods. Exploits OpenMP parallelism (up to 2 cores in the free version). |
| **CODEGEN** | CODE GENerator | Translates user-defined models from text descriptions into Fortran 2003 code for compilation and linking. Supports excitation controllers, torque controllers, injectors, and two-port components. |

## Repository Structure

The documentation is a modular LaTeX project. The main entry point is `stepss_doc.tex`, which includes the following chapters:

- `overview.tex` — Quick overview of STEPSS
- `install.tex` — Installation instructions
- `network.tex` — Network modeling (buses, lines, transformers)
- `ref_and_init.tex` — Reference frame and initialization
- `pfc-data.tex` — PFC module data format
- `files.tex`, `solvsett.tex` — File formats and solver settings
- `disturbances.tex` — Disturbance specification
- `disc_cont.tex`, `sync_thev_impload.tex` — Dynamic models
- `user_models.tex` — User-defined models (CODEGEN)
- `library_blocks.tex` — Library of modeling blocks
- `codegen/` — Individual block definitions

## Building the PDF

Compile with `pdflatex` (run twice to resolve cross-references):

```bash
pdflatex stepss_doc.tex
pdflatex stepss_doc.tex
```

A pre-built PDF (`stepss_doc.pdf` / `userguide.pdf`) is included in this repository.

## Prerequisites (running STEPSS)

STEPSS runs on **Windows 64-bit** and requires:

- **Java 20** (64-bit) — required for the GUI
- No separate installation needed: download `STEPSS.jar` and run it directly; it self-extracts at startup

To compile user-defined models (CODEGEN):

- **Visual Studio 2022 Community** with *Desktop development with C++*
- **Intel oneAPI Fortran Compiler** (BaseKit + Fortran Compiler + HPC Toolkit)

## Limitations (free academic version)

- Maximum **1000 buses/nodes**
- Maximum **2 processor cores** for parallelisation

## License

STEPSS is distributed under the **Academic Public License (APL)**: free for non-commercial use (academic research, teaching, non-profit organisations). Commercial use requires contacting the authors.

PFC and CODEGEN are owned by the authors. RAMSES is owned by the University of Liège (Belgium); the authors hold distribution rights.

## Authors

- **Dr. Petros Aristidou** — petros.aristidou@cut.ac.cy
- **Dr. Thierry Van Cutsem** — thierry.h.van.cutsem@gmail.com
