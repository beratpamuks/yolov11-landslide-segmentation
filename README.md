# Landslide Segmentation with YOLO11m-seg

This repository contains a cleaned version of a landslide image-segmentation project based on Ultralytics YOLO11m-seg and a Roboflow dataset.

## Project scope

The original notebook:
- downloaded a YOLO-format dataset from Roboflow;
- used `yolo11m-seg.pt`;
- checked CUDA availability;
- configured training at 640x640 with batch size 16;
- used AdamW, learning rate `1e-4`, cosine learning-rate scheduling, and weight decay `5e-4`;
- used horizontal/vertical flips, 90-degree rotation, and HSV augmentation;
- evaluated segmentation and bounding-box metrics;
- generated inference predictions.

## Important reproducibility and security notes

- The original notebook contained a Roboflow API key. The cleaned notebook removes the secret and requests it at runtime.
- If the exposed key is still active, revoke/rotate it in Roboflow before publishing this repository.
- The original notebook snapshot does not establish that the configured 100 epochs fully completed. Final metrics should only be added after a completed run with saved artifacts.
- The original notebook created a custom YAML and empty dataset folders, but the actual training call used Roboflow's downloaded `data.yaml`. The cleaned notebook uses that same dataset YAML directly.
- The original prediction code pointed to the training image directory. The cleaned notebook targets the test split when available.

## Repository structure

```text
.
├── notebooks/
│   ├── Landslide_Segmentation_Clean.ipynb
│   └── original/
│       └── Landslide_Segmentation_Project_original.ipynb
├── configs/
├── docs/
├── requirements.txt
└── .gitignore
```

## Results

Final project metrics will be added only from a verified completed training/evaluation run. Do not mix reported values from external papers or presentations with metrics reproduced by this notebook.
