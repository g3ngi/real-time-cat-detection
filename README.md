# Cat Detection AOL Project  
**Real-Time Cat Detection Using YOLO Models**

## 1. Project Overview
This project focuses on building and evaluating a **real-time cat detection system** using modern YOLO-based object detection models. The main objective is to detect cats accurately in images or video streams while maintaining performance suitable for real-time or edge deployment scenarios.

---

## 2. Objectives
The objectives of this project are:

1. To train a cat detection model using a labeled dataset.
2. To evaluate the detection performance using standard object detection metrics.
3. To compare selected YOLO models for accuracy, robustness, and real-time feasibility.
4. To maintain a modular and well-documented workflow for easier experimentation and reproducibility.

---

## 3. Problem Statement
Detecting cats automatically in images or video streams can support various smart monitoring applications such as:

- Pet monitoring at home
- Garden or outdoor cat activity observation
- Smart surveillance and event detection
- Edge AI deployment for low-latency detection

However, real-world detection is challenging because of:

- Occlusion
- Low lighting conditions
- Motion blur
- Background clutter
- Small object sizes
- Unusual cat poses

This project investigates how well YOLO-based detectors handle these challenges.

---

## 4. Dataset
This project uses a cat detection dataset prepared in YOLO-compatible format.

### Dataset Variants
- **`Cats-1`**: Original dataset
- **`Cats-1_clahe`**: CLAHE-enhanced dataset for image contrast improvement

### Why Two Dataset Variants
Using both the original and CLAHE-enhanced versions helps evaluate whether image enhancement can improve model detection performance, especially under difficult lighting or low-contrast conditions.

---

## 5. Models Used
This project compares the following models:

- **YOLO26n Built-in Enhancement**
- **YOLOv26n + CLAHE**

### Reason for Model Selection
These models were chosen because they are designed for real-time object detection and are suitable for computer vision and edge AI applications. The comparison helps determine which model offers a better balance between:

- Detection accuracy
- Inference speed
- Robustness under challenging conditions
- Suitability for real-time deployment

---

## 6. Methodology

### 6.1 Workflow
The overall workflow of this project is:

1. Prepare the dataset
2. Use the original dataset (`Cats-1`) and the CLAHE-enhanced dataset (`Cats-1_clahe`)
3. Train baseline YOLO models
4. Validate and test the models
5. Compare performance metrics
6. Perform qualitative error analysis
7. Analyze model robustness on difficult samples

### 6.2 Training and Validation
The training, validation, and testing workflow is handled in the notebook:

- **`train_validate_test.ipynb`**

This notebook includes the end-to-end experiment process, including:
- Dataset loading
- Model training
- Validation
- Testing
- Result inspection

### 6.3 Evaluation Metrics
The following metrics are used to evaluate the models:

- **mAP@0.5**
- **mAP@0.5:0.95**
- **Precision**
- **Recall**
- **Qualitative Detection Results**

These metrics provide both quantitative and practical insight into model performance.

---

## 7. Project Structure
The project currently uses the following structure:

```bash
.
├── Cats-1/
├── Cats-1_clahe/
├── runs/
├── README.md
└── train_validate_test.ipynb
```

### Structure Explanation
- **`Cats-1/`** contains the original cat detection dataset.
- **`Cats-1_clahe/`** contains the CLAHE-enhanced version of the dataset.
- **`runs/`** stores training results, model checkpoints, validation outputs, and experiment logs.
- **`train_validate_test.ipynb`** is the main notebook used for training, validation, and testing.
- **`README.md`** provides documentation for the project.

---

## 8. Code Modularity
Although this project currently uses a notebook-based workflow, modularity is still reflected through separation of responsibilities inside the experiment process:

- Dataset preparation
- Training
- Validation
- Testing
- Result comparison

For future improvement, this notebook-based workflow can be further modularized into separate Python scripts such as:
- `train.py`
- `evaluate.py`
- `predict.py`
- `utils.py`

### Why Modularity Matters
Modular code and structured workflow provide several advantages:

- Easier debugging
- Better readability
- Reusable components
- Easier extension for future experiments
- Cleaner documentation and maintenance

This is especially important for academic and project-based evaluation.

---

## 9. Installation

### 9.1 Clone the Repository
```bash
git clone https://github.com/your-username/cat-detection-aol.git
cd cat-detection-aol
```

### 9.2 Create Virtual Environment
```bash
python -m venv venv
```

Activate the environment:

**Windows**
```bash
venv\Scripts\activate
```

**Linux / Mac**
```bash
source venv/bin/activate
```

### 9.3 Install Dependencies
```bash
pip install -r requirements.txt
```

> If `requirements.txt` is not yet available, install the needed packages manually based on the notebook imports.

---

## 10. Example Dependencies
Possible dependencies used in this project include:

```txt
ultralytics
opencv-python
matplotlib
numpy
pandas
PyYAML
torch
torchvision
notebook
```

---

## 11. How to Run the Project

### 11.1 Open the Notebook
```bash
jupyter notebook
```

Then open:

```bash
train_validate_test.ipynb
```

### 11.2 Run the Experiment
Execute the notebook cells in order to:

1. Load the dataset
2. Train the selected YOLO model
3. Validate the model
4. Test the model
5. Compare results from different datasets or models

---

## 12. Experimental Setup

### Common Settings
The project compares:
- **YOLOv26n vs YOLOv26n**
- **Original dataset vs CLAHE-enhanced dataset**

This allows the analysis to cover:
- Model comparison
- Dataset preprocessing impact
- Detection robustness under different visual conditions

### Fair Comparison Principle
To ensure a fair comparison, both models should be trained under comparable settings:
- Same dataset split
- Same image resolution
- Same number of epochs
- Same evaluation metrics
- Same training pipeline

---

## 13. Results

> Replace the placeholder values below with your actual experimental results.

| Model   | Prepocessing        | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
|--------|----------------|----------:|-------:|---------:|-------------:|
| YOLOv26n | Yolo Default        | 0.9813 | 0.9745 | 0.9830 | 0.8462 |
| YOLOv26n | CLAHE   | 0.9740 | 0.9617 | 0.9925 | 0.8616 |

### Summary of Findings
- Compare whether YOLOv26n or YOLOv26 + CLAHE performs better.
- Compare whether CLAHE preprocessing improves detection results.
- Highlight which setup is best for difficult conditions such as low contrast or cluttered scenes.

---

## 14. Error Analysis
Error analysis helps explain why the model fails in certain cases.

### Common Failure Cases
Some detection failures may occur because of:

- **Occlusion**  
  Cats partially hidden behind objects are harder to detect.

- **Background Clutter**  
  Complex scenes with plants, furniture, shadows, or similar textures may confuse the model.

- **Small Object Size**  
  Cats appearing far from the camera may have very small bounding boxes.

- **Unusual Poses**  
  Cats lying down, curled up, or partially visible may not match common training examples.

- **Lighting Conditions**  
  Low-light or low-contrast conditions reduce visual clarity.

- **Motion Blur**  
  Fast movement in video frames can reduce detection confidence.

### Interpretation
These errors suggest that model performance depends not only on architecture, but also on dataset diversity and real-world scene complexity.

---

## 15. Model Robustness
Robustness refers to how well the model performs on noisy, challenging, or out-of-distribution data.

### Robustness Evaluation Factors
The model is analyzed on samples containing:

- Blur
- Poor lighting
- Non-frontal cat poses
- Busy backgrounds
- Partial visibility
- Low-contrast images

### Robustness Discussion
A robust model should still detect cats with acceptable confidence even when conditions differ from ideal training samples. If performance drops significantly in these situations, it indicates that further improvements may be needed, such as:

- Data augmentation
- More diverse training samples
- Hyperparameter tuning
- Better generalization strategies

The inclusion of `Cats-1_clahe` also helps examine whether contrast enhancement improves model robustness.

---

## 16. Future Improvements
Possible improvements for future work include:

1. Refactoring notebook code into modular Python scripts
2. Adding a dedicated `requirements.txt`
3. Testing on real-time video streams or CCTV footage
4. Applying more data augmentation strategies
5. Measuring FPS on deployment hardware
6. Integrating the detector into a smart monitoring system

---




