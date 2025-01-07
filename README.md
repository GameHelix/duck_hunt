# Parcel Damage Detection Using YOLOv8

This project implements a computer vision system for automatically detecting and classifying damaged parcels using YOLOv8, helping logistics companies improve their quality control processes.

## Project Overview

The system uses YOLOv8 to detect and classify parcels into two categories:
- Damaged parcels
- Intact parcels

### Key Features

- Real-time parcel damage detection
- Binary classification (damaged/intact)
- Built on YOLOv8 architecture
- GPU-accelerated training and inference
- High accuracy performance (~93% mAP50-95)

## Model Performance

- mAP50: 0.936 (93.6%)
- mAP50-95: 0.930 (93.0%)

Per-class performance:
- Damaged parcels: 92.8% mAP50-95
- Intact parcels: 93.1% mAP50-95

## Getting Started

### Prerequisites

```bash
pip install -r requirements.txt
```

Main dependencies:
- ultralytics==8.3.58
- torch>=2.4.1
- opencv-python
- numpy
- pandas

### Directory Structure

```
parcel_detection/
│
├── dataset/
│   ├── images/
│   │   ├── train/
│   │   └── val/
│   └── labels/
│       ├── train/
│       └── val/
│
├── runs/
│   └── detect/
│       └── train/
│           └── weights/
│               ├── best.pt
│               └── last.pt
│
└── dataset.yaml
```

### Training the Model

```python
from ultralytics import YOLO

# Load the model
model = YOLO('yolov8n.pt')

# Train the model
results = model.train(
    data='dataset.yaml',
    epochs=50,
    imgsz=640,
    batch=16,
    workers=4
)
```

### Inference

```python
from ultralytics import YOLO

# Load trained model
model = YOLO('runs/detect/train/weights/best.pt')

# Perform inference
results = model.predict('path_to_image.jpg')
```

## Model Architecture

Based on YOLOv8n (nano version):
- Parameters: ~3M
- Processing time per image: ~5.8ms
  - Preprocess: 0.1ms
  - Inference: 2.3ms
  - Loss calculation: 0.1ms
  - Postprocess: 3.3ms

## Dataset

The dataset consists of labeled images of parcels, split into:
- Training set: 433 images
- Validation set: 109 images

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Acknowledgments

- [Ultralytics](https://github.com/ultralytics/ultralytics) for YOLOv8
- Kaggle for computing resources
- Dataset contributors

## Contact

Ismat Samadov - [GitHub Profile](https://github.com/Ismat-Samadov)

Project Link: [https://github.com/Ismat-Samadov/parcel_detection](https://github.com/Ismat-Samadov/parcel_detection)
