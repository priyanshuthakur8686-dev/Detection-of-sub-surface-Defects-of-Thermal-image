#🔍 Detection of Sub-surface Defects from Thermal Images
#📌 Overview
Sub-surface defects—such as cracks, voids, delaminations, and corrosion—often remain hidden beneath the surface of materials. While invisible to the naked eye, they can cause serious safety hazards in engineering structures, machinery, and infrastructure.
Thermal imaging offers a non-destructive testing (NDT) method to detect these anomalies by capturing temperature differences that may indicate underlying issues.

This project presents an automated defect detection pipeline that uses computer vision techniques to process infrared thermal images, identify potential defects, and highlight them for further analysis.

#🚩 Problem Statement
Industrial components, pipelines, aerospace structures, and civil engineering constructions can develop hidden defects over time due to:

Material fatigue

Corrosion

Mechanical stress

Environmental degradation

Traditional inspection methods such as manual visual checks or ultrasonic testing have limitations:

Manual methods are subjective and inconsistent.

Ultrasonic/X-ray methods require expensive equipment and skilled operators.

Many techniques are time-consuming and not scalable for large structures.

An automated, fast, and reliable method is needed for early-stage defect detection to prevent catastrophic failures.

#🎯 Objectives
The main goals of this project are:

Develop an automated defect detection system for thermal images.

Ensure noise removal while preserving defect edges.

Implement a robust edge detection algorithm suitable for low-contrast thermal images.

Visualize detection results in a clear and interpretable format for engineers and inspectors.

#💡 Proposed Solution
Our solution integrates image preprocessing, noise filtering, and contour detection into a single processing pipeline.
Key highlights:

Bilateral filtering for edge-preserving noise removal.

Canny edge detection for identifying defect boundaries.

Morphological operations for cleaning the detected edges.

Contour overlay to highlight defects clearly.

This approach ensures a balance between detection accuracy and computational efficiency, making it suitable for real-time or batch analysis.

#🛠️ Methodology
Step 1: Image Acquisition
Thermal images are captured using an Infrared Thermal Camera.
(Example Image)

arduino
Copy
Edit
[Place sample thermal image here]
Step 2: Preprocessing
Convert to Grayscale to reduce computational complexity.

Apply Bilateral Filter to remove noise while preserving edges.

python
Copy
Edit
blurred = cv2.bilateralFilter(gray, 9, 75, 75)
Step 3: Edge Detection
Use Canny edge detection with tuned thresholds (40, 120).

python
Copy
Edit
edges = cv2.Canny(blurred, 40, 120)
Step 4: Morphological Filtering
Apply closing operation to bridge small gaps in edges.

python
Copy
Edit
kernel = np.ones((3, 3), np.uint8)
edges_clean = cv2.morphologyEx(edges, cv2.MORPH_CLOSE, kernel, iterations=2)
Step 5: Contour Extraction
Extract external contours of the detected regions.

Overlay contours in red on the grayscale image.

Step 6: Visualization
Display results in table format:

Grayscale Image

Denoised Image

Edges Detected

Final Crack Detection

#📊 Results
Stage	Output Description
Grayscale Image	Raw infrared image converted to grayscale.
Denoised Image	Bilateral filter applied to preserve edges while reducing noise.
Edges Detected	Canny edge detection output showing possible defect outlines.
Final Detection	Contours highlighted in red on grayscale image for clear defect visualization.

(Example Output Images)

csharp
Copy
Edit
[Place 2x2 subplot result here]
#🚀 Future Scope
This project can be extended to:

Deep Learning Models: Use CNNs or Vision Transformers for automatic defect classification.

Real-time Processing: Integrate into industrial inspection systems with live camera feeds.

Multi-Spectral Analysis: Combine thermal data with visible light images for enhanced accuracy.

3D Defect Mapping: Use multiple images to reconstruct defect geometry.

#📂 Dataset
The thermal images used in this project can be:

Captured using FLIR or Seek Thermal cameras.

Obtained from public infrared datasets such as:

FLIR Thermal Dataset

Infrared Thermographic Image Dataset (ITID)

#🖥️ Implementation Details
Languages & Tools
Python 3.8+

OpenCV – Image processing

NumPy – Numerical operations

Matplotlib – Visualization

Code Structure
bash
Copy
Edit
📁 thermal-defect-detection
 ┣ 📜 defect_detection.py   # Main detection script
 ┣ 📜 README.md             # Project documentation
 ┣ 📂 images/               # Sample input thermal images
 ┣ 📂 results/              # Output defect detection results
 ┗ 📜 requirements.txt      # Dependencies
📥 Installation & Usage
bash
Copy
Edit
# Clone the repository
git clone https://github.com/<your-username>/thermal-defect-detection.git
cd thermal-defect-detection

# Install dependencies
pip install -r requirements.txt

# Run the detection script
python defect_detection.py
📜 License
This project is licensed under the MIT License – you are free to use, modify, and distribute it.

🙌 Acknowledgements
OpenCV and NumPy developers for their amazing libraries.

Research studies on Infrared Thermography and NDT for background inspiration.

The thermal imaging community for making datasets available.

🧑‍💻 Author
Priyanshu Singh
B.Tech in Electronics & Communication Engineering
National Institute of Technology, Goa

📧 Email: priyanshuthakur8686@gmail.com
🔗 LinkedIn: https://shorturl.at/6XLNS
