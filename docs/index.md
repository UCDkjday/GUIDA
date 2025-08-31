---

# docs/index.md (for GitHub Pages)

---

## layout: default title: GUIDA — Graphical User Interface for Data Analysis

# GUIDA — Graphical User Interface for Data Analysis

**A Python GUI for electrophysiology analysis built on the NWB standard.**\
**Pipelines:** PSD (Welch / MNE) • PAC (MNE + TensorPAC) • Rich plotting • Reproducible exports

## Get Started

1. **Install**
   ```bash
   conda create -n ResearchGUI python=3.11 -y
   conda activate ResearchGUI
   pip install -r requirements.txt
   ```
2. **Launch**
   ```bash
   python app.py   # replace with your entry point
   ```
3. **Load NWB files** and explore plots, PSD, and PAC.

## Features

- Convert Neuralynx **NCS → NWB**, aggregating per‑session channels and metadata.
- Interactive **DearPyGui** plots (multi‑panel, synced, band‑pass filtering, axis control).
- **PSD** via MNE’s Welch; metrics include broadband power, TDR, aperiodic exponent.
- **PAC** via TensorPAC; outputs comodulograms, peak frequencies, SNR, z‑score trends.
- Export **PNG/PDF/SVG/EPS** + parameterized reports for reproducibility.

## Frequency Bands

Delta (1–4 Hz), Theta (4–12 Hz), Beta (12–30 Hz), Gamma (30–80 Hz), High Gamma (80–200 Hz)

## Links

- 👉 [README](../README.md)
- 📦 Releases (add link when available)
- 🧪 Example Data (add link when available)

---

### How to publish this site

1. Create a `docs/` folder and add this `index.md` (and any images in `docs/assets/`).
2. In **GitHub → Settings → Pages**, set **Source = **`` on the default branch.
3. Choose a theme (optional) and save. Your site will build in a minute or two.
