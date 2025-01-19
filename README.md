# Tomato Leaf Disease Detection using YOLO Models

This project implements and compares three YOLO architectures (YOLOv8n, YOLOv9s, and YOLO11s) for detecting diseases in tomato leaves. The models are trained to identify 7 different conditions: Bacterial Spot, Early Blight, Healthy, Late Blight, Leaf Mold, Target Spot, and Black Spot.

## Dataset Overview

![image](https://github.com/user-attachments/assets/0430a3fd-41de-4b17-8d31-1cc6bca9c06d)

The dataset consists of annotated tomato leaf images split into training, validation, and test sets. Each image is labeled with bounding boxes indicating disease locations and types.

### Class Distribution

![image](https://github.com/user-attachments/assets/a999cc0d-efc3-4991-823e-459735586fec)

### Sample Images

1. ![image](https://github.com/user-attachments/assets/d382cdf5-70dc-4d29-b3b0-8e2175dd4f17)

2. ![image](https://github.com/user-attachments/assets/c927230b-e578-4ca3-8236-64fd5a11195d)

### Disease Co-occurrence

The following matrix shows how different diseases tend to appear together in images:

![image](https://github.com/user-attachments/assets/32da4dc8-9f7e-488f-9c27-c3b3c8d3382d)

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

1. Confusion matrix for YOLOv8 on Test Set:
![image](https://github.com/user-attachments/assets/dda003c7-6848-49bf-aa48-352ddeb8ecb2)

2. Confusion matrix for YOLOv9 on Test Set:
![image](https://github.com/user-attachments/assets/24e0bb4c-52c9-48d3-b4d6-fb761fd39be4)

3. Confusion matrix for YOLO11 on Test Set:
![image](https://github.com/user-attachments/assets/390ad727-0856-4fef-9883-661fd7430f7b)

### Precision-Recall Curves

1. Precision-Recall curve for YOLOv8 on Test Set:
![image](https://github.com/user-attachments/assets/7386ec34-4bd0-4501-8352-13e684a67164)

2. Precision-Recall curve for YOLOv9 on Test Set:
![image](https://github.com/user-attachments/assets/3b44f8d0-401a-470d-b823-5f7d4127962d)

3. Precision-Recall curve for YOLO11 on Test Set:
![image](https://github.com/user-attachments/assets/55a64467-78e2-4214-ae3f-523d033b635a)

## Comprehensive Model Analysis

### Performance Metrics Deep Dive

#### Speed vs Accuracy Analysis
1. **YOLOv8n**
   - Fastest inference at 13.4ms
   - Highest mAP50: 0.774
   - Best choice for real-time applications
   - Smallest model (3M parameters) making it ideal for edge devices
   - Processing breakdown:
     * Preprocess: 2.6ms (19.4%)
     * Inference: 13.4ms (70.2%)
     * Postprocess: 3.1ms (10.4%)

2. **YOLOv9s**
   - Slowest inference at 23.7ms
   - Highest mAP50-95: 0.489
   - Mid-sized model (7.2M parameters)
   - Processing breakdown:
     * Preprocess: 3.1ms (10.5%)
     * Inference: 23.7ms (80.3%)
     * Postprocess: 2.7ms (9.2%)

3. **YOLO11s**
   - Moderate inference at 17.7ms
   - Lowest overall performance
   - Largest model (9.4M parameters)
   - Processing breakdown:
     * Preprocess: 3.2ms (13.7%)
     * Inference: 17.7ms (75.6%)
     * Postprocess: 2.5ms (10.7%)

### Model Size Comparison

- YOLOv8n: 3.0M parameters
- YOLOv9s: 7.2M parameters
- YOLO11s: 9.4M parameters

## Results and Visualization

> YOLO11 makes two false positive predictions
![image](https://github.com/user-attachments/assets/42f0197e-c263-4e45-a674-eeb0af6860a7)

> YOLOv8 has the highest confidence
![image](https://github.com/user-attachments/assets/be052675-02f3-42fe-a6a1-b7412b25cf3f)

## References

1. https://github.com/ultralytics
2. https://www.kaggle.com/datasets/farukalam/tomato-leaf-diseases-detection-computer-vision/data?select=train
3. https://learnopencv.com/performance-comparison-of-yolo-models/
