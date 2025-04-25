# Project Explainer: Multi-Spectral Band Visualization Before Cloud Detection

## 🌍 Overview
This project demonstrates how to visualize and process multi-spectral satellite data to extract insights, focusing particularly on RGB and NDVI (Normalized Difference Vegetation Index) composites, followed by a simple but effective cloud detection method. It aims to show how clouds affect land analysis and how masking them can enhance interpretation.

## 📥 Dataset
We work with five satellite scenes, each stored as a `.npy` NumPy array containing multiple bands of Sentinel-2 imagery. Each array includes at least the following bands:

- B02 (Blue)  - Index 1
- B03 (Green) - Index 2
- B04 (Red)   - Index 3
- B08 (NIR)   - Index 7
- B11 (SWIR)  - Index 11

## 🎯 Objective
1. Visualize RGB and NDVI composites for all scenes
2. Detect and mask clouds using spectral thresholding
3. Apply the cloud mask to RGB & NDVI
4. Save and export the clean, enhanced visual outputs

## 🧪 Step-by-Step Breakdown

### 🔹 RGB Composite Visualization
- We extract Red, Green, and Blue bands from each scene.
- Normalize each band individually for better contrast.
- Stack the normalized bands to create a natural-color image.

### 🔹 NDVI Calculation
- NDVI = (NIR - Red) / (NIR + Red)
- This index highlights vegetation health — green areas have high NDVI values.

### 🔹 Cloud Detection (Rule-Based)
- Clouds appear bright in visible and NIR, and dark in SWIR.
- We apply this rule:
```python
cloud_mask = (
    (scene[1] > 0.25) &   # Blue
    (scene[2] > 0.25) &   # Green
    (scene[3] > 0.25) &   # Red
    (scene[7] > 0.25) &   # NIR
    (scene[11] < 0.3)     # SWIR
)
```

### 🔹 Mask Application
- The boolean mask is applied to RGB and NDVI arrays.
- Cloudy pixels are blacked out (or turned to NaN / 0).

### 🔹 Exporting Results
- Each RGB and NDVI output (with/without clouds) is saved as `.png`.
- Images are organized by scene in the `outputs/` folder.

## 📈 Insights & Impact
- **Before cloud masking**, NDVI can mislead interpretation in cloudy zones.
- **After cloud masking**, we get cleaner, more reliable vegetation data.
- This process simulates pre-processing workflows used in climate science, forestry, agriculture, and land use analysis.

## 🛠️ Tech Stack
- Python (NumPy, Matplotlib)
- Google Colab (for development)
- Sentinel-2 multi-band data

## 🚀 What I Learned
- Improved handling of multi-spectral datasets
- How band combinations affect imagery
- How simple rules can effectively detect atmospheric obstructions
- Modular, scalable scripting for geospatial workflows

## 📦 Folder Structure (Simplified)
```
data/        -> Input .npy scenes
outputs/     -> Exported PNG visualizations
notebooks/   -> Workflow notebook
utils/       -> Helper functions
README.md    -> Project overview
documentation/ -> This explainer doc
```

## 🌐 Real-World Application
This project simulates essential pre-processing for:
- Deforestation monitoring
- Agriculture yield forecasting
- Urban development impact analysis
- Disaster relief & damage detection

## 💡 Future Improvements
- Use ML for cloud classification
- Add time-series analysis
- Integrate GIS tools like QGIS or rasterio for geo-referenced outputs

---

This project shows how even with simple logic and open data, we can uncover deep insights from our planet. It's a strong portfolio piece for Earth observation, climate tech, or geospatial data science.

---

