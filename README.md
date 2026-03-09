# CEOS Best Practice Guidance: Integrating Multiplatform and Multisensor Data for Water Science and Applications

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.placeholder.svg)](https://doi.org/10.5281/zenodo.placeholder)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ceos-org/ceos-water-guidance/main)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ceos-org/ceos-water-guidance)

**CEOS SIT Chair Priority 1 — Water Planet**  
Lead: 

Version: 0.1-draft | Status: Open for community review

---

## What This Repository Is

This repository contains the **CEOS Best Practice Guidance for Integrating Multiplatform and Multisensor Satellite Data for Water Science and Applications** — a living, community-maintained technical resource developed under the CEOS Strategic Implementation Team (SIT) Chair Priority 1: Water Planet.

It provides:
- **Written guidance** (Markdown documents) on combining optical and SAR satellite data to derive water variables
- **Executable notebooks** (Jupyter/Python) demonstrating each integration approach with real satellite data
- **Gap analysis** of current observational capabilities and in-situ network adequacy

This resource is structured for two audiences:
- **Practitioners and scientists** who need actionable, reproducible methods for water monitoring
- **CEOS member agencies** coordinating future satellite mission planning and product standards

---

## How to Use This Resource

### Read the guidance documents
Browse the [`/docs`](./docs) folder or visit the rendered website: [ceos-org.github.io/ceos-water-guidance](https://ceos-org.github.io/ceos-water-guidance) *(coming soon)*

### Run the notebooks interactively
Click **"launch binder"** or **"Open in Colab"** above — no installation required.

Or clone locally:
```bash
git clone https://github.com/ceos-org/ceos-water-guidance.git
cd ceos-water-guidance
pip install -r requirements.txt
jupyter lab
```

---

## Repository Structure

```
ceos-water-guidance/
│
├── README.md                          ← This file
├── CONTRIBUTING.md                    ← How to contribute
├── LICENSE                            ← CC BY 4.0
├── requirements.txt                   ← Python dependencies
├── environment.yml                    ← Conda environment
│
├── docs/                              ← Written guidance (Markdown)
│   ├── 00_introduction.md
│   ├── 01_satellite_overview.md       ← Optical, SAR, complementary missions
│   ├── 02_integration_protocols.md    ← Fusion methods, uncertainty, ARD standards
│   ├── 03_gap_analysis.md             ← Variable-by-variable capability assessment
│   ├── 04_insitu_adequacy.md          ← Cal/val network assessment
│   ├── 05_best_practices.md           ← Consolidated recommendations
│   ├── 06_use_cases.md                ← Socio-economic applications
│   │
│   ├── terrestrial/                   ← Part I: Terrestrial Water Cycle
│   │   ├── surface_water.md
│   │   ├── soil_moisture.md
│   │   ├── snow_ice.md
│   │   ├── evapotranspiration.md
│   │   └── groundwater.md
│   │
│   └── water_quality/                 ← Part II: Water Quality
│       ├── overview.md
│       ├── chlorophyll_habs.md
│       ├── turbidity_sediment.md
│       ├── cdom.md
│       └── inland_coastal.md
│
├── notebooks/                         ← Executable Jupyter notebooks
│   ├── terrestrial/
│   │   ├── 01_surface_water_flood_mapping.ipynb
│   │   ├── 02_soil_moisture_downscaling.ipynb
│   │   ├── 03_evapotranspiration_estimation.ipynb
│   │   ├── 04_snow_cover_SWE.ipynb
│   │   └── 05_groundwater_GRACE.ipynb
│   │
│   └── water_quality/
│       ├── 06_chlorophyll_HABs_detection.ipynb
│       ├── 07_turbidity_suspended_sediment.ipynb
│       └── 08_cdom_inland_water_quality.ipynb
│
├── data/                              ← Small sample datasets for notebooks
│   └── README.md                      ← Links to full datasets on Earthdata/Copernicus
│
└── gap_analysis/                      ← Machine-readable gap assessment
    ├── variables_matrix.csv           ← Variable × capability scoring table
    └── insitu_networks.csv            ← In-situ network inventory
```

---

## Scope

This guidance covers:

**Part I — Terrestrial Water Cycle** *(Lead: John Bolten, NASA GSFC)*
- Surface water extent and storage
- Soil moisture (surface and root-zone)
- Snow, ice, and cold season processes
- Evapotranspiration
- Groundwater (GRACE-FO based)

**Part II — Water Quality** *(Lead: Mahya Ghazi Zadeh Hashemi)*
- Chlorophyll-a and harmful algal blooms (HABs)
- Turbidity and total suspended sediment
- Colored dissolved organic matter (CDOM)
- Inland and near-coastal water quality

**Cross-cutting**
- Optical + SAR data fusion protocols
- CEOS Analysis Ready Data (CEOS-ARD) alignment
- Gap analysis of water variables
- In-situ network and cal/val adequacy assessment

---

## Key Satellite Missions Covered

| Type | Missions |
|---|---|
| Optical multispectral | Landsat 8/9, Sentinel-2, MODIS, VIIRS |
| Ocean color / hyperspectral | PACE, Sentinel-3 OLCI, HICO |
| Thermal IR | Landsat TIR, ECOSTRESS, Sentinel-3 SLSTR |
| SAR C-band | Sentinel-1 A/B/C, RADARSAT-2 |
| SAR L-band | ALOS-2 PALSAR-2, NISAR |
| Passive microwave | SMAP, AMSR2, SMOS |
| Surface water / altimetry | SWOT, ICESat-2 |
| Gravity / groundwater | GRACE-FO |
| Precipitation | GPM, GOES-R, Meteosat |

---

## Contributing

We welcome contributions from CEOS member agencies, associated partners, and the broader water science community.

**Ways to contribute:**
- 🐛 **Flag a gap or error:** [Open an issue](https://github.com/ceos-org/ceos-water-guidance/issues)
- ✏️ **Improve a guidance section:** Fork the repo, edit the `.md` file, submit a pull request
- 📓 **Add or improve a notebook:** See [CONTRIBUTING.md](./CONTRIBUTING.md) for notebook standards
- 🌍 **Add a regional use case:** Submit a notebook or section addition for your region or application

All contributors are listed in [CONTRIBUTORS.md](./CONTRIBUTORS.md) and credited in the Zenodo DOI record.

---

## Team

| Name | Affiliation | Role |
|---|---|---|
| Erin Urquhart Jephson | NASA HQ | SIT Chair Priority 1 Lead, Organizer |
| John D. Bolten | NASA GSFC | Lead, Terrestrial Water Cycle |
| Mahya Hashemi | NASA GSFC | Lead, Terrestrial Water Cycle |
| Cecile S. Rousseaux | NASA GSFC | Lead, Water Quality |
| Perry C. Oddo | NASA LaRC | Coordination, stakeholder engagement |
| Morgaine McKibben | NASA GSFC | Lead, Terrestrial Water Cycle |
| Karen St. Germain | NASA ESD | CEOS SIT Chair |
| Julie Robinson | NASA ESD | CEOS SIT Co-Chair |


---

## Citation

If you use this guidance or notebooks in your work, please cite:



---

## License

Documentation and notebooks are released under the
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license,
consistent with the CEOS-ARD repository and other CEOS open publications.

---

## Related CEOS Resources

- [CEOS-ARD Repository](https://github.com/ceos-org/ceos-ard) — Analysis Ready Data Product Family Specifications
- [CEOS SAR Guide](https://github.com/ceos-org/ceos-sar-guide) — Layman's guide to SAR data (Jupyter notebook format)
- [CEOS Water Strategy 2015](https://ceos.org/observations/documents/CEOS_Water_Strategy_2015_V1.pdf)
- [Future of CEOS-ARD Concept Note (2025)](https://ceos.org/ard/files/Future%20of%20CEOS-ARD%20Concept%20Note.pdf)
- [CEOS SIT Chair Priority 1: Water Planet](https://ceos.org/document_management/Meetings/Plenary/39/Presentations/10.3_SIT_Chair_Priorities_NASA.pptx)
