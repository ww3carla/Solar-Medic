```markdown
# SolarMedic AI

## Overview

SolarMedic AI is a deep learning project focused on detecting and diagnosing anomalies in photovoltaic modules using infrared images.

The project uses a two-step approach. First, a binary CNN model predicts whether a solar module is normal or anomalous. Then, for anomalous modules, a second CNN model predicts the most likely anomaly type.

The project also includes a demonstrative maintenance-priority system, which assigns an inspection priority based on the predicted anomaly.

---

## Objectives

- Analyze infrared images of photovoltaic modules
- Perform exploratory data analysis (EDA)
- Build a binary anomaly detection model
- Train a multi-class anomaly diagnosis model
- Evaluate model performance using classification metrics
- Create a simple inspection-support workflow for solar module maintenance

---

## Dataset

The dataset used is the **Infrared Solar Modules dataset**, which contains thermal images of photovoltaic modules.

The dataset includes:

- 20,000 infrared images
- Image size: 24 × 40 pixels
- Grayscale thermal images
- 12 total classes

Classes:

- `No-Anomaly`
- `Cell`
- `Cell-Multi`
- `Cracking`
- `Diode`
- `Diode-Multi`
- `Hot-Spot`
- `Hot-Spot-Multi`
- `Offline-Module`
- `Shadowing`
- `Soiling`
- `Vegetation`

Target variables created for this project:

- `binary_status`
  - `Normal`
  - `Anomaly Detected`

- `maintenance_priority`
  - `Low`
  - `Moderate`
  - `High`
  - `Critical`

---

## Workflow

1. **Data Preparation**
   - Load image metadata
   - Validate image paths
   - Create a structured dataset manifest
   - Generate binary anomaly labels
   - Define maintenance-priority categories

2. **Exploratory Data Analysis**
   - Analyze class distribution
   - Visualize infrared image samples
   - Inspect pixel intensity patterns
   - Identify class imbalance

3. **Binary Anomaly Detection**
   - Train a baseline CNN model
   - Improve the model using augmentation, batch normalization and dropout
   - Use a recall-oriented threshold to reduce missed anomalies

4. **Multi-Class Anomaly Diagnosis**
   - Train a CNN model on anomalous samples only
   - Predict the anomaly category
   - Apply class weighting to handle imbalanced classes

5. **Final SolarMedic AI Workflow**
   - Detect whether a module is normal or anomalous
   - Predict the anomaly type for suspicious modules
   - Assign a demonstrative maintenance priority
   - Generate an inspection-style output

---

## Results

### Binary Anomaly Detection

The baseline binary CNN achieved:

- Accuracy: 82.20%
- Anomaly recall: 72.13%
- F1-score: 80.21%
- ROC-AUC: 90.75%

The improved binary CNN achieved:

- Accuracy: 86.17%
- Anomaly recall: 93.67%
- F1-score: 87.13%
- ROC-AUC: 95.56%

The improved model reduced missed anomalous modules from 418 to 95, making it more suitable for an inspection-support scenario.

### Multi-Class Anomaly Diagnosis

The anomaly diagnosis CNN achieved:

- Accuracy: 59.27%
- Macro F1-score: 55.20%
- Weighted F1-score: 59.73%

The model performed better on classes such as `Diode`, `Diode-Multi`, `Cracking` and `Shadowing`.

Rare or visually similar classes, such as `Hot-Spot`, `Hot-Spot-Multi`, `Soiling` and `Cell-Multi`, were more difficult to classify.

---

## Key Findings

- Infrared images contain useful patterns for detecting photovoltaic module anomalies.
- Binary anomaly detection performs better than detailed multi-class diagnosis.
- Class imbalance strongly affects anomaly classification performance.
- A recall-oriented threshold is useful in maintenance screening because missed anomalies are more costly than additional inspections.
- The final system should be interpreted as a decision-support prototype, not as a fully autonomous industrial diagnostic system.

---

## Limitations

- The images have a low resolution of 24 × 40 pixels.
- The dataset is strongly imbalanced across anomaly classes.
- The split is image-based, since site-level identifiers are not available.
- The maintenance-priority mapping is demonstrative and not an official photovoltaic maintenance standard.
- Some anomaly classes are visually similar and difficult to distinguish reliably.

---

## Technologies Used

- Python
- pandas
- numpy
- matplotlib
- Pillow
- scikit-learn
- TensorFlow / Keras
- Jupyter Notebook

---

## Project Status

This project was developed as a deep learning prototype for photovoltaic thermal inspection.

Future improvements could include:

- Testing the model on higher-resolution thermal images
- Using site-level validation
- Improving performance on rare anomaly classes
- Experimenting with transfer learning
- Deploying the workflow as a simple web application
```
