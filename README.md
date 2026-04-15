# Synthetic Darkened Object Detection Benchmark: YOLOv26 vs RT-DETR
Overview

This repository contains experiments comparing two object detection paradigms:

YOLOv26 (CNN-based detector)
RT-DETR (Transformer-based detector)

The focus of this study is to evaluate model performance under:

Normal lighting conditions
Synthetic low-light (darkened) conditions

The goal is to analyze robustness and performance degradation across lighting conditions.

Methodology
1. Data Preparation
Start from a base dataset (CCPD)
Apply filtering and preprocessing
Generate synthetic low-light images using brightness reduction

This results in two datasets:

Normal dataset
Low-light dataset

2. Training Setup

Both models are trained under comparable conditions:
- Same dataset split
- Same input resolution
- Similar training epochs and batch size (as much as architecture allows)
YOLOv26
- One-stage CNN detector
- Faster convergence
- Typically lighter and more efficient
RT-DETR
- Transformer-based detector
- End-to-end detection (no NMS required)
- Heavier but potentially more robust in complex scenarios

3. Evaluation Metrics
- mAP (mean Average Precision)
- Precision / Recall
- Performance comparison across:
  - Normal condition
  - Low-light condition

#Key Research Question
How do CNN-based and Transformer-based object detectors behave under degraded lighting conditions?

## How to Run

### 1. Install Dependencies

```bash
pip install ultralytics
pip install torch torchvision
```

### 2. Run YOLOv26

Open and execute:

```
YOLOv26.ipynb
```

### 3. Run RT-DETR

Open and execute:

```
RTDETER.ipynb
```

## Notes

* Ensure dataset paths are correctly configured in both notebooks
* Training RT-DETR may require more GPU memory than YOLOv26
* Some hyperparameters may need adjustment due to architectural differences

### Training Set Performance

| Model   | Normal  | Low-Light |
| ------- | ------- | --------- |
| RT-DETR | 0.9728 | 0.9508   |
| YOLOv26 | 0.9862 | 0.9606   |

### Test Set Performance

| Model   | Normal    | Low-Light  |
| ------- | --------- | ---------- |
| RT-DETR | 0.9718  | 0.9415  |
| YOLOv26 | 0.985   | 0.9571 |

## Analysis

* YOLOv26 consistently outperforms RT-DETR in both normal and low-light conditions
* Both models experience performance degradation under low-light conditions
* RT-DETR shows slightly larger degradation, indicating higher sensitivity to lighting changes

However, note that:

* The performance gap is relatively small (~1–2%)
* Results may depend heavily on dataset size and augmentation strategy


## Limitations

* Synthetic low-light may not fully represent real-world conditions
* Dataset size may impact generalization
* Direct comparison is constrained by architectural differences


## Future Work

* Use real low-light datasets
* Explore advanced augmentation techniques
* Optimize RT-DETR for limited resources


## License

This project is for research and academic purposes.
