🌳 Forest Regeneration Prediction using Satellite Imagery

This project focuses on monitoring and predicting forest regeneration and encroachment patterns in the Dandakaranya region of Chhattisgarh, India. Using multi-year satellite data and machine learning models, we aim to support data-driven decision-making for environmental policy and conservation.

📂 Dataset

Due to GitHub's file size limitations, the full dataset (\~40 GB) has been uploaded externally and can be accessed (https://drive.google.com/drive/folders/107v4QCFWR8yb6K4PIF4Z-uZRF9NEAHE4?usp=drive_link)
The dataset consists of:

* Multi-temporal satellite imagery (2011–2020)
* GRVI and other vegetation indices
* Ground-truth shapefiles (if applicable)
* PREPROCESSED DATA - https://drive.google.com/drive/folders/1a4nogYngdtdBU_XxNMz6Jvg5Rmk2spmx?usp=drive_link
 🧠 Methods Used

* QGIS for spatial analysis and preprocessing
* Python for data handling, ML modeling, and visualization
* Classification algorithms (e.g., Random Forest, XGBoost) for land cover change detection
* Time-series analysis for regeneration trend prediction
🌳 Step-by-Step in QGIS:
✅ 1. Load Your Raster
Load each .tif image into QGIS.

Ensure it has Band 2 (Blue), Band 3 (Green), and Band 4 (Red).

✅ 2. Calculate GRVI (Green-Red Vegetation Index)
Formula:

GRVI
=
Green
−
Red
Green
+
Red
GRVI= 
Green+Red
Green−Red
​
 
In QGIS:

Go to Raster → Raster Calculator

Set output layer path.

Use expression like this:

perl
Copy
Edit
("your_image@2" - "your_image@3") / ("your_image@2" + "your_image@3")
Where:

@2 is Band 3 (Green)

@3 is Band 4 (Red)

Save result as: grvi_2015.tif, etc.

✅ 3. Threshold GRVI to Binary Forest Map
Use the Raster Calculator again:

perl
Copy
Edit
("grvi_2015@1" > 0.1) * 1
This sets pixels with GRVI > 0.1 as 1 (forest), others as 0 (non-forest).

Save as: forest_mask_2015.tif, etc.

✅ 4. (Optional) Clip to Shapefile AOI
Use:

Raster → Extraction → Clip raster by mask layer

Input raster: forest_mask_2015.tif

Mask: your AOI shapefile
 📊 Outputs


* Regeneration classification maps
* Trend graphs over years
* Model evaluation reports (Accuracy, F1 Score, etc.)

 📌 Project Motivation

India’s forests, particularly in central tribal zones, face pressure from both human encroachment and natural degradation. Timely detection and prediction of regeneration patterns can assist policymakers and environmentalists in planning restoration initiatives.

