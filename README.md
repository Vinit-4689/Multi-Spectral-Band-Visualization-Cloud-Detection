![Mult-spectral band banner](https://github.com/user-attachments/assets/1f098cf3-6471-46cd-8d4e-4c217afac59c)


# Multi-Spectral Band Visualization Before Cloud Detection

This project focuses on visualizing multi-spectral satellite imagery data and detecting clouds using a rule-based masking approach. The output includes RGB composites, NDVI maps, cloud masks, and cloud-masked RGB/NDVI images for five satellite scenes.

---

## 🛰️ Project Overview

- **Goal**: Understand how clouds appear in different spectral bands and apply a basic cloud detection algorithm.
- **Tech Stack**: Python, NumPy, Matplotlib, Google Colab
- **Data Type**: Multi-spectral satellite imagery (13 bands per scene)
- **Scenes Used**: 5 distinct satellite image scenes

---

## 📁 Dataset

- Five `.npy` files representing multi-spectral scenes.
- Each file contains a `(13, H, W)` array: 13 spectral bands for a given scene.
- Uploaded and processed in Google Colab.

---

## 🧪 Processing Steps

1. **Load multi-spectral .npy files**
2. **Normalize** key spectral bands (Blue, Green, Red, NIR, SWIR1)
3. **Generate RGB composites**
4. **Calculate NDVI**
5. **Detect clouds** using a simple threshold-based rule:
    ```python
    cloud_mask = (
        (Blue > 0.25) &
        (Green > 0.25) &
        (Red > 0.25) &
        (NIR > 0.25) &
        (SWIR1 < 0.3)
    )
    ```
6. **Visualize and save**:
   - Original RGB
   - NDVI
   - Cloud masks
   - RGB & NDVI with cloud masking applied

---

## 🖼️ Output Files (per scene)

- `sceneX_rgb.png`: Original RGB
- `sceneX_ndvi.png`: Original NDVI
- `sceneX_cloud_mask.png`: Detected cloud mask
- `sceneX_rgb_masked.png`: RGB with clouds masked (gray)
- `sceneX_ndvi_masked.png`: NDVI with cloud areas set to NaN

---

## 💡 Learnings

- Clouds are bright in visible/NIR but not in SWIR
- Simple rule-based masking works surprisingly well for clear/cloudy scenes
- Visualizing different spectral bands is crucial for remote sensing analysis

---

## 📦 How to Run (Google Colab)

1. Upload all `.npy` files to a folder
2. Load them into a list using `np.load()`
3. Follow the notebook code to process each scene
4. Visualize and export images using `matplotlib`

---

## 📬 Contact

**Vinit Singh Pathir**  
[LinkedIn](https://www.linkedin.com/in/vinit-singh-cse/)  
Feel free to reach out if you want to collaborate on remote sensing, data science, or climate projects!

---

## 🌍 License

This project is open-source and free to use under the MIT License.

