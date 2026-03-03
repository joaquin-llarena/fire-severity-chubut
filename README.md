# 🔥 Fire Severity Assessment in Chubut (Patagonia, Argentina, 2025–2026)  
### NBR & dNBR Analysis using Sentinel-2 Level-2A Imagery  

**Author:** Joaquin Llarena  
**Date:** March 2026  

---

## 🌍 1. Overview

This project presents a geospatial assessment of two major wildfire events that occurred in northwestern Chubut Province (Patagonia, Argentina) during the 2025–2026 fire season.

Using Sentinel-2 Level-2A imagery and spectral indices (NBR and dNBR), the analysis aims to:

- Delineate burned areas  
- Classify fire severity  
- Quantify affected surface area  

The project demonstrates a structured and reproducible geospatial data analysis workflow for wildfire impact assessment.

---

## 🛠️ 2. Tech Stack

**Languages & Environment**
- Python 3  
- Jupyter Notebook (VS Code)

**Geospatial Processing**
- rasterio  
- geopandas  
- shapely  
- QGIS  

**Data Analysis & Visualization**
- numpy  
- pandas  
- matplotlib  

---

## 📍 3. Study Area

The analysis focuses on two wildfire events in Chubut Province, Argentina:

- **Epuyén**  
- **Los Alerces National Park**

Both events affected Andean-Patagonian native forests and wildland–urban interface zones during a high-intensity fire season.

---

## 🛰️ 4. Satellite Data

**Platform:** Sentinel-2 MSI  
**Product Level:** Level-2A (Surface Reflectance)

**Acquisition dates:**
- Pre-fire: 25 November 2025  
- Post-fire: 18 February 2026  

**Tiles used (UTM zones 18S and 19S):**

• `T18GYT` •  `T18GYU`  
• `T19GCN` •  `T19GCP`

All scenes were clipped to predefined Areas of Interest (AOIs) created in QGIS.

> **Note on Data Availability**  
> Raw Sentinel-2 Level-2A products are not included in this repository due to file size constraints.  
> The scenes used in this analysis can be downloaded from the Copernicus Open Access Hub (Copernicus Data Space Ecosystem).

### Spectral Bands

The analysis was conducted at **20 m spatial resolution** using:

- B8A — Narrow Near Infrared  
- B12 — Shortwave Infrared 2  

---

## ⚙️ 5. Methodology

### Normalized Burn Ratio (NBR)

```
NBR = (NIR − SWIR2) / (NIR + SWIR2)
```

Where:
- NIR = B8A  
- SWIR2 = B12  

### Differenced NBR (dNBR)

```
dNBR = NBR_pre − NBR_post
```

Fire severity levels were classified using established threshold ranges from wildfire remote sensing literature.

---

## 🧩 6. Workflow Structure

The analysis is organized into two main notebooks:

### 01 — Sentinel-2 Preprocessing

- SAFE product loading  
- Band extraction  
- CRS verification and harmonization  
- AOI clipping  
- Raster stacking  
- Export of analysis-ready GeoTIFFs  

### 02 — Burn Severity Analysis

- Cloud and shadow masking (SCL band)  
- NBR calculation (pre- and post-fire)  
- dNBR computation  
- Severity classification  
- Area calculation by severity class (hectares and %)  
- Independent clipping per fire foci  

---

## 📊 7. Results

- Delineation of burned area for each fire event  
- dNBR-based severity classification maps  
- Area statistics by severity class (hectares and percentage)  
- Independent analysis of two major fire focus
- Cartographic outputs suitable for technical reporting  

---

## 🗺️ 8. Visual Outputs

The repository includes the following outputs:

- Pre- and post-fire true color composites  
- NBR maps (pre and post)  
- dNBR map  
- Fire severity classification maps  
- Final cartographic layout prepared in QGIS  

<!-- Insert figures below -->

### Outputs

![Final Severity Map Layout](Figures/burn_severity_map_chubut_2025_2026.png)

![Summary](Figures/burn_severity_summary.png)

---

## 🔁 9. Reproducibility & Adaptability

Although developed as a case study focused on the 2025–2026 Chubut wildfires, the workflow is modular and transferable.

With minor adjustments — primarily updating:

- AOIs  
- Acquisition dates  
- Input Sentinel-2 scenes  

the same analytical structure can be applied to other wildfire events or comparable remote sensing assessments.

The notebooks provide a transparent and adaptable framework that can be extended into a fully automated processing pipeline if required.

---

## 📁 10. Repository Structure

```
fire-severity-chubut/
│
├── Data/
│   ├── aoi/                 # Area of Interest shapefiles
│   ├── Raw/
│   │   ├── Pre/             # Pre-fire Sentinel-2 SAFE products (not included)
│   │   └── Post/            # Post-fire Sentinel-2 SAFE products (not included)
│   │
│   └── Processed/
│       ├── Pre/             # Pre-fire processed rasters (not included)
│       ├── Post/            # Post-fire processed rasters (not included)
│       └── Analysis/        # Derived rasters and intermediate outputs (not included)
│
├── Notebooks/
│   ├── 01_sentinel2_preprocessing.ipynb
│   └── 02_burn_severity_analysis.ipynb
│
├── Figures/                 # Figures displayed in this README
├── Outputs/                 # Final cartographic layout (PDF)
│
└── README.md
```
> Raw and processed raster datasets are excluded from version control due to file size limitations.