# Tomato Leaf Disease Detection using YOLO Models

This project implements and compares three YOLO architectures (YOLOv8n, YOLOv9s, and YOLO11s) for detecting diseases in tomato leaves. The models are trained to identify 7 different conditions: Bacterial Spot, Early Blight, Healthy, Late Blight, Leaf Mold, Target Spot, and Black Spot.

## Dataset Overview

[Insert Class Distribution Plot]

The dataset consists of annotated tomato leaf images split into training, validation, and test sets. Each image is labeled with bounding boxes indicating disease locations and types.

### Class Distribution

[Insert detailed class distribution statistics]

### Sample Images

[Insert 2-3 sample images with bounding box annotations]

### Disease Co-occurrence

The following matrix shows how different diseases tend to appear together in images:

[Insert Co-occurrence Matrix]

## Model Architectures

### 1. YOLOv8n

- Parameters: 3,007,013
- Layers: 168
- Inference Speed: 13.4ms
  - Preprocess: 2.6ms
  - Inference: 13.4ms
  - Postprocess: 3.1ms

### 2. YOLOv9s

- Parameters: 7,169,797
- Layers: 486
- Inference Speed: 23.7ms
  - Preprocess: 3.1ms
  - Inference: 23.7ms
  - Postprocess: 2.7ms

### 3. YOLO11s

- Parameters: 9,415,509
- Layers: 238
- Inference Speed: 17.7ms
  - Preprocess: 3.2ms
  - Inference: 17.7ms
  - Postprocess: 2.5ms

## Training Configuration

### Model Parameters

- Image Size: 640x640
- Batch Size: 8
- Epochs: 50
- Number of Classes: 7

### Learning Rate

- Initial: 0.01
- Final: 0.001

### Regularization

- Weight Decay: 0.0005
- Dropout: 0.2

### Data Augmentation

- HSV Adjustments
  - Hue: 0.015
  - Saturation: 0.7
  - Value: 0.4
- Translation: 0.1
- Scale: 0.5
- Horizontal Flip: 0.5

## Performance Metrics

### Test Set Results

| Model   | mAP50 | mAP50-95 |
| ------- | ----- | -------- |
| YOLOv8n | 0.774 | 0.480    |
| YOLOv9s | 0.761 | 0.489    |
| YOLO11s | 0.734 | 0.466    |

### Confusion Matrices

[Insert confusion matrices for each model]

### Precision-Recall Curves

[Insert PR curves for each model]

## Model Comparison Analysis

### Speed vs Accuracy Trade-off

- YOLOv8n offers the best inference speed (13.4ms) and highest mAP50 (0.774)
- YOLOv9s achieves the highest mAP50-95 (0.489) but with slowest inference (23.7ms)
- YOLO11s provides balanced performance with moderate speed (17.7ms)

### Model Size Comparison

- YOLOv8n: 3.0M parameters
- YOLOv9s: 7.2M parameters
- YOLO11s: 9.4M parameters

## Results and Visualization

[Add sample detection results]

## References

1. https://github.com/ultralytics
2. https://www.kaggle.com/datasets/farukalam/tomato-leaf-diseases-detection-computer-vision/data?select=train
3. https://learnopencv.com/performance-comparison-of-yolo-models/
