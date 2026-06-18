# RELION StarVis

A browser-based interactive metadata visualizer and filter for RELION STAR files. No installation required — open `relion_star_visualizer.html` in any modern browser.

---

## Overview

StarVis loads any RELION STAR file (micrographs, particles, or other metadata blocks) and provides histogram, scatter, multi-histogram, and statistics views with interactive, draggable filtering — without needing a running RELION session. It is intended to complement RELION's own `relion_analyse.py` dashboard with zero-installation deployment, freehand subpopulation selection, and direct micrograph preview.

---

## Features

### Loading data
- Upload any `.star` file; multiple `data_` blocks are detected automatically and selectable via a dropdown
- Two built-in sample datasets (synthetic micrographs and particles metadata) let you try the tool without any RELION files
- Optional: load a project root folder so micrograph thumbnails can be resolved from `rlnMicrographName` and shown on hover

### Histogram tab
- Select any numeric column to see its distribution, with adjustable bin count and count/frequency scaling
- Draggable threshold lines directly on the chart, or a dual-thumb range slider below it — bars outside the threshold turn red
- Live statistics: total, filtered count, mean, std, median, min, max

### Scatter tab
- Choose X and Y columns, with optional colour-coding by a third column
- Adjustable point size and maximum point count (with random subsampling above the limit)
- Independent draggable threshold sliders for the X and Y axes; out-of-threshold points turn red
- **Freehand lasso selection**: draw an arbitrary region directly on the plot and filter the dataset to the enclosed points
- **Micrograph hover preview**: when a micrograph folder is loaded, hovering a point shows the corresponding micrograph thumbnail and metadata
- Live statistics: shown/total points, points within threshold, Pearson correlation, and per-axis mean/std

### Multi-histogram tab
Select multiple numeric columns (Ctrl+click) to compare their distributions side by side in a single view.

### Statistics tab
A full per-column table (type, N, mean, std, min, Q1, median, Q3, max, active filter) for every column in the loaded block; clicking a numeric column jumps to its histogram.

### Filtering
- Per-column filters appear in the sidebar with a dual-thumb range slider and numeric min/max fields
- All filters combine (AND logic) across the dataset; an active-filter indicator and count are shown in the header
- Reset all filters or expand all filter panels with one click

### Export
- **Export filtered**: downloads the currently filtered subset
- **PDF report**: generates a formatted PDF summary of the loaded data and current filter state

---

## Getting Started

1. Download `relion_star_visualizer.html` and open it in a browser
2. Click **Upload .star** and select a RELION STAR file, or click one of the **demo** buttons to try it with synthetic data
3. Switch between the Histogram, Scatter, Multi-histogram, and Statistics tabs to explore the data
4. Drag threshold lines or sliders to filter; use **Export filtered** to download the result

---

## File Format Requirements

Any valid RELION STAR file is supported. The parser recognizes `data_` block headers, `loop_` sections, and `_rln*` column definitions; numeric columns are automatically detected for histogram, scatter, and statistics use.

---

## Limitations

- Runs entirely client-side; very large STAR files (hundreds of thousands of rows) may affect browser responsiveness, particularly on the scatter plot
- Micrograph hover preview requires loading a local project folder via the browser's directory picker and matches files by name
- PDF report generation runs in-browser via jsPDF and may take a few seconds for large filtered datasets

---

## License

GNU General Public License v3.0 (GPLv3). See the `LICENSE` file in this repository for the full license text.
