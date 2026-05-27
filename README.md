# XRD-CT Phase Map and Radial Profile Analysis

A Jupyter notebook workflow for processing, visualizing, and extracting radial profiles from spatially resolved X-ray diffraction computed tomography (XRD-CT) phase maps of catalyst pellets.

This notebook is designed for beamstop-processed XRD-CT phase maps exported in a compatible format, where each map represents the spatial distribution of a fitted crystalline phase within the catalyst pellet.

This script was developed using an Nb₂O₅-based catalyst pellet case study as reference; therefore, the default variables, phase dictionaries, mask definitions, and plotting settings follow this example dataset. All of these parameters can be modified and adapted to other beamstop-processed XRD-CT phase maps.

---

## Main features

- Load XRD-CT reconstructed phase maps for multiple catalyst samples or reaction states.
- Organize phase maps by sample and crystalline phase.
- Generate publication-style multi-panel phase map figures.
- Apply optional phase-specific thresholds to reduce low-intensity background.
- Define pellet masks from a selected reference phase, such as `Nb2O5 orthorhombic`.
- Clean pellet masks by retaining the largest connected component, filling internal holes/cracks, and applying binary closing.
- Compute distance-to-surface radial coordinates:
  - `r/R = 0` for the pellet core
  - `r/R = 1` for the outer pellet region
- Calculate radial profiles for selected phases across different catalyst states.
- Plot multi-panel radial profiles with consistent styling and sample ordering.
- Generate diagnostic plots showing:
  - phase maps with iso-contours,
  - radial binning histograms,
  - distance-to-surface radial profiles.
- Export figures for publication, reports, or thesis documentation.

---

## Input data

The expected input consists of beamstop-processed XRD-CT phase maps exported in a compatible format (e.g., .h5).

Each phase map should represent the spatial distribution of a fitted crystalline phase for a given sample or catalyst state. In the current example dataset, the phase maps are organized by sample name and phase name, for example:

```python
all_data[sample_name][phase_name]
```

Example phase names may include:

```text
Nb2O5 orthorhombic
Nb2O5 tetragonal
Ru
RuO2
Graphite
```

The exact phase names, dictionaries, thresholds, and colormaps can be changed by the user.

---

## Case-study note

This script was developed using an Nb₂O₅-based catalyst pellet case study as reference; therefore, the default variables, phase dictionaries, mask definitions, and plotting settings follow this example dataset. All of these parameters can be modified and adapted to other beamstop-processed XRD-CT phase maps.

---

## Installation

### Option 1 — Conda / Mamba

```bash
conda env create -f environment.yml
conda activate xrdct-radial-profile
jupyter notebook
```

or:

```bash
jupyter lab
```

### Option 2 — pip + virtual environment

```bash
python -m venv .venv
```

#### Windows

```bash
.venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook
```

#### macOS / Linux

```bash
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook
```

---

## Requirements

Recommended Python version:

```text
Python 3.10 or newer
```

Main Python packages:

```text
numpy
scipy
matplotlib
h5py
jupyter
notebook
ipykernel
```

Optional, depending on the exact notebook version:

```text
pandas
tifffile
scikit-image
```

---

## Running the notebook

After installing the environment, open the notebook:

```bash
jupyter notebook
```

or:

```bash
jupyter lab
```

Then run the cells in order:

1. Import packages.
2. Define input paths and phase names.
3. Load the XRD-CT phase maps.
4. Plot phase maps.
5. Generate pellet masks.
6. Compute radial profiles.
7. Generate diagnostic iso-contour plots.
8. Export figures.

---

## Output files

Depending on the selected options, the notebook can export figures such as:

```text
phase_profiles.png
radial_profiles_filledmask.png
radial_schematic.png
```

A possible output folder structure is:

```text
project_folder/
├── notebook.ipynb
├── data/
│   └── beamstop_processed_phase_maps/
├── figures/
│   ├── phase_profiles.png
│   ├── radial_profiles_filledmask.png
│   └── radial_schematic.png
└── results/
```

---

## Repository layout

```text
xrdct-radial-profile-analysis/
├── XRDCT_phase_map_radial_profile_analysis.ipynb
├── README.md
├── LICENSE
├── CITATION.cff
├── requirements.txt
├── environment.yml
├── .gitignore
└── figures/
    ├── phase_profiles.png
    ├── radial_profiles_filledmask.png
    └── radial_schematic.png
```

---

## Known limitations

- The notebook assumes that phase maps have already been reconstructed and fitted before analysis.
- The current example is based on an Nb₂O₅ catalyst pellet dataset, so phase names and default dictionaries need to be changed for other systems.
- The radial profile is based on a distance-to-surface coordinate, not a center-based radius.
- The quality of the radial profile depends on the quality of the pellet mask.
- Very noisy or fragmented reference phase maps may require manual threshold adjustment.
- Input paths and output paths should be adapted by the user before running the notebook.

---

## Citation

Please cite the software using the metadata provided in `CITATION.cff`.

---

## License

This repository is distributed under the MIT License.
