#🏗️ Multimodal Bridge Defect Detection with Cross-Verification

Welcome to the repository for our IEEE-published pilot study on structural health monitoring of bridges using a multimodal data fusion framework. This project introduces a novel integration of Non-Destructive Evaluation (NDE) signals with adaptive image processing to accurately detect and verify bridge defects. The framework was developed, tested, and validated using real-world data sourced from the Federal Highway Administration’s InfoBridge platform.

🔍 Overview

Bridges across the globe are aging rapidly, and traditional inspection techniques often fall short in detecting subsurface defects like delamination, cracking, or debonding. This project addresses this challenge by:

Fusing Impact Echo (IE) and Ultrasonic Surface Waves (USW) datasets to pinpoint defect-prone areas.
Applying Alpha Shape Analysis (ASA) to extract overlapping regions indicating structural anomalies.
Validating these defect zones through adaptive image processing techniques.
Reducing false positives through spatial and visual cross-verification.
This method enhances reliability, localization accuracy, and minimizes manual interpretation.

🧠 Core Methodology

**1. Data Acquisition**
We use two key NDE techniques:

Impact Echo (IE): Detects internal defects such as voids and cracks using peak frequency analysis.
Ultrasonic Surface Waves (USW): Measures concrete elasticity to identify surface degradation or stiffness loss.
Both datasets were downloaded from the InfoBridge portal for a selected bridge (e.g., I-220 over John R. Lynch Street in Mississippi).

**2. Data Preprocessing & Feature Extraction**
IE data (voltage arrays) is converted to frequency domain using Fast Fourier Transform (FFT).
USW data is processed to calculate the elasticity modulus using time-delay estimation and wave velocity formulas.

**3. Defect Filtering Using K-Means**
K-means clustering (K=3) segments both datasets.
IE: Detects low-frequency regions.
USW: Detects low-modulus areas.
Thresholds from clustering help isolate high-risk zones.

**4. Multimodal Fusion with Alpha Shapes**
We apply Alpha Shape Analysis (ASA) to each modality.
The intersection of αIE and αUSW defines common defect-prone zones.
These zones are spatially contextualized using unified lane boundaries.

**5. Image-Based Cross Verification**
Contour images of IE and USW from InfoBridge are processed:
HSV-based color masking detects red-yellow regions indicating potential defects.
Morphological operations (e.g., erosion/dilation) remove noise.
Bounding boxes are created around significant contours.
Detected defects are mapped to real-world coordinates.
Fused data from multimodal analysis is overlaid on these processed images to verify alignment.

**6. Evaluation Metrics**
Precision: 0.75
Recall: 0.92
F1-score: 0.83
These metrics are computed using micro-averaging across IE and USW fusion results.

📌 Tools & Technologies Used

Python
NumPy, Pandas – Data handling
OpenCV – Image processing
Matplotlib & Seaborn – Visualization
Scikit-learn – Clustering (K-Means)
Alpha Shape (alphashape package) – Geospatial boundary modeling

📊 Key Visualizations

The paper and notebook include:

IE & USW contour plots
Alpha shape overlays
Common defective zones from fusion
Bounding boxes from image verification
Final fused and cross-validated defect locations

📚 Citation

If you use this framework or its concepts in your own work, please cite the original paper:

Ravi Datta Rachuri, Duoduo Liao, Samhita Sarikonda, Datha Vaishnavi Kondur,
"A Multimodal Fusion Framework for Bridge Defect Detection with Cross-Verification",
IEEE International Conference on Big Data 2024. DOI: 10.1109/BigData62323.2024.10825867

🚀 Future Work

Integrate real-time data ingestion for live monitoring.
Expand framework to include Infrared Thermography or Ground Penetrating Radar.
Improve image alignment accuracy using deep learning-based segmentation.
Deploy as a dashboard-based decision support tool for field inspectors.
🙌 Acknowledgments

This project was supported by the **Federal Highway Administration (FHWA)**. We thank FHWA for providing open access to bridge condition datasets and InfoBridge tools that enabled this research.

