# [DRAFT] GUIDA — *Graphical User Interface for Data Analysis*

> **One‑liner:** A Python GUI for exploring and analyzing large electrophysiology datasets in the NIH‑compliant NWB format — with pipelines for PSD and PAC, rich plotting, and reproducible, shareable outputs.

---

## Table of Contents

- [Overview](#overview)
- [Why GUIDA?](#why-guida)
- [Features](#features)
- [Frequency Bands](#frequency-bands)
- [Screenshots](#screenshots)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Workflows](#workflows)
  - [1) Convert Neuralynx NCS → NWB](#1-convert-neuralynx-ncs--nwb)
  - [2) Import NWB files](#2-import-nwb-files)
  - [3) Plot raw & filtered signals](#3-plot-raw--filtered-signals)
  - [4) Compute Power Spectral Density (PSD)](#4-compute-power-spectral-density-psd)
  - [5) Compute Phase–Amplitude Coupling (PAC)](#5-compute-phaseamplitude-coupling-pac)
  - [6) Export figures & reports](#6-export-figures--reports)
- [Outputs & Reproducibility](#outputs--reproducibility)
- [Roadmap](#roadmap)
- [Citing / References](#citing--references)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## Overview

GUIDA is a Python application with a graphical user interface designed to make analysis of large electrophysiological datasets accessible and reproducible. It targets workflows commonly used in systems neuroscience — notably Power Spectral Density (PSD) and Phase–Amplitude Coupling (PAC) — and standardizes data I/O around **Neurodata Without Borders (NWB)**, an NIH‑endorsed, shareable format.

The tool enables:

- Non‑programmers to browse, filter, and analyze data interactively.
- Programmers to extend pipelines in a modular way.
- Research groups to exchange data and results using a consistent, open standard (NWB).

## Features

- **NCS → NWB conversion** for Neuralynx recordings (aggregates 64‑channel sessions; inserts key metadata such as rat IDs and voltage scaling ratios).
- **NWB file browser** with persisted file locations and summary metadata.
- **Interactive plotting** (DearPyGui): multiple synchronized plots, pan/zoom, axis locks, numeric axis limits, band‑pass filtering to visually hunt frequency‑specific events.
- **PSD pipeline** (Welch via MNE): broadband power, theta\:delta ratio (TDR), aperiodic exponent, and related metrics.
- **PAC pipeline** (MNE preprocessing + TensorPAC): comodulograms with optional preprocessing and algorithm choices; reports peak phase/amplitude frequencies, SNR, and z‑score trends.
- **Figure export** to **PNG / PDF / SVG / EPS** with customizable size, DPI, color palettes, axes limits, opacity, filenames, and output locations.
- **Reports** capturing parameters, algorithm progression, and numerical results for candidate biomarkers.

## Screenshots

(Add images in `docs/assets/` and reference here.)

- GUI overview — file browser and plots
- PSD example — raw vs filtered, metrics overlay
- PAC example — comodulogram with peak markers

## Tech Stack

- **Language:** Python
- **Data format:** NWB via **PyNWB**
- **Signal processing:** **MNE**, **SciPy**
- **PAC:** **TensorPAC**
- **Plots & export:** **Matplotlib**
- **GUI:** **DearPyGui**

## Installation

> Replace the placeholders below with your actual steps (e.g., `conda env create -f environment.yml`).

### Option A — Conda (recommended)

```bash
# 1) Create environment
conda create -n ResearchGUI python=3.11 -y
conda activate ResearchGUI

# 2) Install dependencies
# If you have an environment.yml, prefer this:
# conda env update -n ResearchGUI -f environment.yml

pip install -r requirements.txt
```

### Option B — Pip only

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Quick Start

```bash
# 1) Launch the app (replace with your entry point)
python app.py
# or
python -m guida
```

- Open **Import** tab → pick your **NWB** folder (optionally save path for next launch)
- Select a file → view metadata → open plot windows
- Use **PSD** and **PAC** panels to configure parameters → run → view figures and reports

## Workflows

### 1) Convert Neuralynx NCS → NWB

- Select an input folder; the converter recursively discovers **.ncs** files.
- All channels for a single recording session are aggregated into **one NWB** file.
- Inserts metadata such as rat IDs and voltage scaling ratios.

> **CLI tip (optional):** If you expose the converter as a script, document it here, e.g.
>
> ```bash
> python scripts/convert_ncs_to_nwb.py --input /path/to/ncs_root --output /path/to/nwb_out
> ```

### 2) Import NWB files

- Point GUIDA at a folder; all **.nwb** files become available via file paths.
- Persist this location to auto‑populate on startup.

### 3) Plot raw & filtered signals

- Add one or many channels from any NWB file into one or multiple plots.
- Band‑pass filters (lowpass/highpass) help eyeball frequency‑specific events.
- Rich interactivity: drag to pan, scroll to zoom, lock axes, set exact axis limits, and synchronize multiple plots.

### 4) Compute Power Spectral Density (PSD)

- PSD is computed via **MNE’s Welch** implementation.
- Derived metrics include **broadband power**, **theta****:delta**** ratio (TDR)**, and **aperiodic exponent**.

### 5) Compute Phase–Amplitude Coupling (PAC)

- Preprocessing in **MNE**; PAC via **TensorPAC**.
- Highly configurable (frequency grids, preprocessing choices, coupling estimators).
- Outputs **comodulograms**, **peak phase / amplitude frequencies**, **band SNR**, and **z‑score trends**.

### 6) Export figures & reports

- Export **PNG/PDF/SVG/EPS** with precise control of size/DPI/colors/axes.
- Save parameterized **reports** for PSD and PAC runs to ensure reproducibility.

## Outputs & Reproducibility

- Every figure/report writes the **parameters and metadata** needed to regenerate it.
- Data are standardized as **NWB**, enabling validation or re‑analysis in other tools.
- Consider committing **small example NWB files** and **unit tests**; keep large datasets out of the repo using `.gitignore` and/or Git LFS.

## Roadmap

-

## Citing / References

> **Your Thesis** — *Title, Institution, Year.*\
> Author: *Your Name*.\
> (Replace this block with your finalized citation.)

Key libraries used: **PyNWB**, **MNE**, **SciPy**, **TensorPAC**, **Matplotlib**, **DearPyGui**.\


## License

Choose a license and add `LICENSE` to the repo (e.g., MIT or BSD‑3‑Clause). Update this section accordingly.

## Acknowledgments

Developed in the **Gurkoff Lab**, UC Davis School of Medicine. Built with gratitude to the open‑source neuroscience community.
