# 🌍 Satellite Image Segmentation with U-Net  

## 📌 Project Description  
This project focuses on **semantic segmentation of satellite images** using a **U-Net deep learning model**.  
The dataset consists of **multi-spectral images (.tif format)** with **12 channels**, each providing unique information about land, vegetation, water, and atmospheric conditions.  
The goal is to detect and segment **water bodies** from multi-spectral satellite data.  

---

## 🛰️ Dataset and Channels  
Each input image has **12 spectral bands** and auxiliary layers. Below is a summary of the main channels:  

| Channel | Wavelength / Data | Function |
|---------|------------------|----------|
| **Coastal Aerosol** | ≈ 0.43 µm | Detects tiny atmospheric particles, useful for haze/smoke removal and shallow water analysis. |
| **Blue** | ≈ 0.49 µm | Penetrates water, helps in depth & quality analysis, vegetation/urban studies. |
| **Green** | ≈ 0.56 µm | Sensitive to chlorophyll, used for vegetation monitoring. |
| **Red** | ≈ 0.66 µm | Strongly absorbed by vegetation; combined with NIR for NDVI. |
| **NIR (Near Infrared)** | ≈ 0.84 µm | Vegetation health & biomass, distinguishes water (appears dark). |
| **SWIR1** | ≈ 1.6 µm | Sensitive to soil/vegetation moisture, drought and fire mapping. |
| **SWIR2** | ≈ 2.2 µm | Distinguishes snow, ice, clouds, used in geology & burnt area mapping. |
| **QA Band** | Metadata | Quality mask for cloud, shadow, snow filtering. |
| **Elevation (DEM)** | External | Provides elevation, slope, hydrological analysis. |
| **Land Cover (ESA World Cover)** | Classification | Urban, forest, cropland, grassland, water. |
| **Water Occurrence Probability** | Derived | Frequency of water presence over time. |
| **Binary Water Mask** | Derived | 1 = water, 0 = not water, used as training labels. |

📷 Example of dataset channels:  
![Spectral Channels](Untitled.jpeg)  

---

## 🧠 Model  
- **Architecture:** U-Net (encoder-decoder structure with skip connections).  
- **Input size:** `128 × 128 × 12` (all spectral channels used).  
- **Output:** Binary mask (water vs non-water).  
- **Loss Function:** Binary Crossentropy.  
- **Optimizer:** Adam.  

---

## 📊 Metrics  
The model was evaluated using multiple segmentation metrics:  

- **Accuracy** → Overall classification performance.  
- **Dice Coefficient (F1 Score for segmentation)** → Measures overlap between prediction and ground truth.  
- **IoU (Intersection over Union)** → Evaluates overlap of predicted vs actual segmentation.  
- **Loss (Binary Crossentropy)** → Training and validation loss.  

---

## 📈 Results  
- Training achieved **~92% validation accuracy**.  
- **Dice coefficient** reached **~0.82**.  
- **IoU** improved steadily to **~0.70**.  
- Validation loss stabilized around **0.21 – 0.23**.  

✅ These results indicate that the U-Net model effectively segments water bodies from multi-spectral satellite images.  
