# Introduction

## Background and Context

Earth's water cycle is under increasing pressure from climate change, population growth, and competing demands across agriculture, energy, ecosystems, and human settlements. Satellite remote sensing has become an indispensable tool for monitoring water resources at scales and frequencies impossible to achieve with ground-based networks alone.

Two complementary families of satellite sensors now provide the foundation for water monitoring from space:

- **Optical sensors** (multispectral, hyperspectral, thermal) measure reflected and emitted electromagnetic radiation across visible and infrared wavelengths. They excel at characterizing surface water extent, water quality, land surface temperature, and vegetation water stress under clear-sky conditions.

- **Synthetic Aperture Radar (SAR) sensors** transmit and receive microwave energy, penetrating clouds and acquiring data regardless of solar illumination. They provide unique sensitivity to soil moisture, surface roughness, vegetation structure, and surface water under all-weather conditions.

Neither sensor family alone is sufficient. Optical sensors are blind under cloud cover — a critical limitation for flood mapping and agricultural monitoring in tropical and monsoon regions. SAR sensors lack the spectral information needed for water quality retrievals. **The integration of optical and SAR data — combining their complementary strengths — unlocks capabilities that neither can achieve independently.**

This principle is well understood in the remote sensing community, but fragmented guidance on *how* to implement these integrations operationally has limited uptake. Practitioners face inconsistent preprocessing standards, undocumented fusion workflows, and a lack of reproducible examples. Decision-makers lack clear evidence that integrated products are more reliable than single-sensor alternatives.

This guidance document addresses that gap directly.

---

## Purpose

This document provides **practical, community-endorsed best practice guidance** for combining optical and SAR satellite data to derive water variables for science and operational applications. It is a deliverable of the CEOS Strategic Implementation Team (SIT) Chair Priority 1: Water Planet — developed under the CEOS mandate to coordinate satellite Earth observation for societal benefit.

Specifically, this guidance aims to:

1. Document proven and emerging methods for integrating optical and SAR data for each major water variable
2. Identify current gaps in observational capability and in-situ network adequacy
3. Provide reproducible, executable examples that practitioners can adapt for their own applications
4. Align with CEOS Analysis Ready Data (CEOS-ARD) standards to ensure interoperability
5. Serve as a technical foundation for the CEOS-ARD for Water product specifications being developed under the CEOS-ARD Strategy 2026

---

## Scope

### Variables Covered

This guidance addresses two domains:

**Part I: Terrestrial Water Cycle** covers the physical variables that describe where water is stored and how it moves through the land surface:

| Variable | Why Optical+SAR Integration Matters |
|---|---|
| Surface water extent and storage | SAR provides cloud-free flood mapping; optical provides spectral discrimination of water vs. shadow |
| Soil moisture | SAR backscatter provides spatial detail; passive microwave provides physical constraint |
| Snow cover and snow water equivalent | Optical NDSI for extent; SAR for wet/dry discrimination and SWE approximation |
| Evapotranspiration | Thermal IR provides LST; optical provides vegetation fraction; SAR provides soil moisture constraints |
| Groundwater | GRACE-FO provides total water storage; optical/SAR constrain surface and soil water for signal isolation |

**Part II: Water Quality** covers the optical and biogeochemical properties of inland, coastal, and ocean waters:

| Variable | Why Multi-sensor Integration Matters |
|---|---|
| Chlorophyll-a and harmful algal blooms | Bio-optical algorithms require multi-band optical; SAR detects surface accumulations |
| Turbidity and suspended sediment | Broadband optical inversion; cross-mission calibration critical for time series |
| Colored dissolved organic matter (CDOM) | UV-visible absorption; linked to dissolved carbon and light attenuation |
| Inland and near-coastal water quality | High spatial resolution optical required; atmospheric correction is the critical challenge |

### What This Guidance Does Not Cover

- Hydrological or ocean circulation modeling (guidance is on observation inputs, not model internals)
- Policy or governance of water management
- Proprietary or classified satellite data
- Real-time operational systems (guidance is on methods, not system architectures)

---

## Audience

This guidance is written for three overlapping audiences:

**Remote sensing and water science practitioners** — scientists, engineers, and analysts who work directly with satellite data and need technically detailed, reproducible methods. The Jupyter notebooks in the `/notebooks` directory are written primarily for this audience.

**Water resource managers and operational agencies** — decision-makers who need to understand what satellite data can and cannot tell them, how to evaluate product quality, and how to connect EO data to their information needs. The written guidance sections are designed to be accessible without requiring deep remote sensing expertise.

**CEOS member agencies and coordination bodies** — the agencies and working groups responsible for planning future satellite missions, developing product standards, and coordinating international observing systems. The gap analysis (Section 3) and CEOS-ARD alignment material (Section 2.4) are written specifically for this audience.

---

## How This Document Is Organized

This repository is structured so that each section can be read independently, but the sections build on each other:

```
docs/
├── 01_satellite_overview.md       ← What sensors exist, what they measure, their characteristics
├── 02_integration_protocols.md   ← How to combine them: preprocessing, fusion, uncertainty
├── 03_gap_analysis.md            ← What the current satellite fleet cannot yet do
├── 04_insitu_adequacy.md         ← Whether in-situ networks can support cal/val
├── 05_best_practices.md          ← Consolidated recommendations by variable
├── 06_use_cases.md               ← Real-world applications with socio-economic context
│
├── terrestrial/                  ← Detailed guidance per terrestrial variable
└── water_quality/                ← Detailed guidance per water quality variable
```

Each variable section in `terrestrial/` and `water_quality/` has a companion executable notebook in `notebooks/` that demonstrates the methods described.

---

## Relationship to Other CEOS Activities

This guidance is intentionally designed to connect with and reinforce three other active CEOS workstreams:

**CEOS-ARD Strategy 2026** — The Future of CEOS-ARD Concept Note (October 2025) identifies *Thematic and Higher-level CEOS-ARD Products* as a priority, explicitly targeting water applications. This BPG defines the science requirements and integration methods that should inform what CEOS-ARD for Water product specifications require. We are coordinating directly with the CEOS-ARD Oversight Group to ensure alignment.

**CEOS SAR Guide** (`ceos-org/ceos-sar-guide`) — This repository uses the same format (Markdown + Jupyter notebooks) established by the SAR Guide. Water scientists who have used the SAR Guide will find the structure immediately familiar. Several notebooks in this repository extend the SAR Guide's examples into water-specific applications.

**CEOS Water Strategy 2015** — This document responds directly to CEOS Water Strategy recommendations C.1, C.6, C.10, E.1, E.5, E.7, and E.8, providing the technical guidance that those recommendations called for but left unspecified.

---

## How to Contribute

This document is designed to grow with the community. The most important gaps in current coverage — particularly for cold season processes, small water body detection, and water quality in the Global South — will only be filled with contributions from agencies and researchers with direct expertise in those areas.

See [CONTRIBUTING.md](../CONTRIBUTING.md) for full instructions. In brief:

- **To flag an error or gap:** [Open a GitHub issue](https://github.com/ceos-org/ceos-water-guidance/issues)
- **To improve a section:** Fork the repository, edit the `.md` file, and submit a pull request
- **To add a notebook:** Follow the notebook template in `notebooks/TEMPLATE.ipynb`
- **To add a regional use case:** Submit a new file under `docs/use_cases/`

All contributors are credited in the repository commit history and in the Zenodo DOI record.

---

## Version History

| Version | Date | Status | Notes |
|---|---|---|---|
| 0.1-draft | April 2026 | Open for community review | Initial structure; terrestrial sections in progress |
| 0.5-draft | September 2026 | Internal CEOS review | SIT Technical Workshop |
| 1.0-rc | November 2026 | CEOS Plenary review | Release candidate |
| 1.0 | 2027 | CEOS Endorsed | Final endorsed version |
