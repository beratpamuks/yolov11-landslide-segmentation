# Technical audit of the original notebook

## Confirmed from the uploaded notebook

- Roboflow is used for dataset download.
- Model: `yolo11m-seg.pt`.
- GPU check: CUDA / Tesla T4 was available in the recorded run.
- Training configuration: 100 epochs, 640 image size, batch 16, device 0, AdamW, lr0 0.0001, cosine LR, weight decay 0.0005, fliplr 0.5, flipud 0.5, degrees 90, hsv_s 0.5, hsv_v 0.4.
- Training uses `dataset.location + "/data.yaml"`.
- Validation uses `model.val()`.
- Prediction uses confidence threshold 0.6 and saves outputs.

## Problems corrected in the cleaned version

1. API key was embedded directly in source code.
2. A manually created YAML was not the YAML actually passed to training.
3. Empty `/content/dataset/...` directories were created but were not part of the actual Roboflow training pipeline.
4. The prediction variable was called `test_image`, but the source pointed to `/train/images`.
5. The cleaned notebook reads class metadata from the actual dataset YAML instead of hard-coding `nc=1`.
6. Validation and test evaluation are separated.
7. The final notebook records configuration without embedding credentials.

## Claims that should NOT yet be made

- Do not claim the original notebook completed all 100 epochs unless a completed run artifact is available.
- Do not claim final mAP/F1 values from a presentation or external paper as results reproduced by this notebook unless they can be traced to this exact experiment.
