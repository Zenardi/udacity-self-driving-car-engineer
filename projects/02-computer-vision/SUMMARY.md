# Object Detection in an Urban Environment — Experiment Summary

## Project Overview

This project trains object detection models using the [TensorFlow Object Detection API](https://tensorflow-object-detection-api-tutorial.readthedocs.io/) and AWS SageMaker on the [Waymo Open Dataset](https://waymo.com/open/) to detect **3 classes**: Vehicle, Pedestrian, and Cyclist.

Three pretrained COCO models were fine-tuned with 2,000 training steps each, deployed in SageMaker, and evaluated on a held-out validation set via COCO-standard metrics.

---

## Experiments

### Experiment 1 — SSD MobileNet v2 FPNLite 640×640

| Parameter | Value |
|---|---|
| Pre-trained checkpoint | `ssd_mobilenet_v2_fpnlite_640x640_coco17_tpu-8` |
| Training steps | 2,000 |
| Batch size | 8 |
| Instance | ml.trn1.2xlarge |
| Optimizer | SGD + Momentum (0.9) |
| Learning rate | 0.08, cosine decay, warmup=1,000 steps |
| Augmentations | `random_horizontal_flip`, `random_crop_image` |

**Training Loss Progression**

| Step | Total Loss |
|---|---|
| ~500  | 0.993 |
| ~700  | 0.762 |
| ~900  | 0.759 |
| ~1,100 | 0.686 |
| ~2,000 | ~0.68 |

**Evaluation Metrics (at step 2,000)**

| Metric | Value |
|---|---|
| **mAP (IoU 0.50–0.95)** | **10.31%** |
| mAP @ IoU=0.50 | 22.00% |
| mAP @ IoU=0.75 | 9.03% |
| mAP — small objects | 4.55% |
| mAP — medium objects | 34.90% |
| mAP — large objects | 53.23% |
| AR @ 100 proposals | 16.00% |

**Inference Animation**: [`mobilenet/data/animation.gif`](mobilenet/data/animation.gif)

---

### Experiment 2 — SSD ResNet50 v1 FPN 640×640

| Parameter | Value |
|---|---|
| Pre-trained checkpoint | `ssd_resnet50_v1_fpn_640x640_coco17_tpu-8` |
| Training steps | 2,000 |
| Batch size | 8 |
| Instance | ml.p3.2xlarge |
| Optimizer | SGD + Momentum (0.9), bfloat16 |
| Learning rate | 0.04, cosine decay, warmup=2,000 steps |
| Augmentations | `random_horizontal_flip`, `random_crop_image` |

**Training Loss Progression**

| Step | Total Loss |
|---|---|
| ~200  | 1.444 |
| ~400  | 1.106 |
| ~600  | 1.100 |
| ~800  | 0.867 |
| ~1,000 | 0.998 |
| ~2,000 | ~0.87 |

**Evaluation Metrics (at step 2,000)**

| Metric | Value |
|---|---|
| **mAP (IoU 0.50–0.95)** | **6.32%** |
| mAP @ IoU=0.50 | 12.04% |
| mAP @ IoU=0.75 | 6.21% |
| mAP — small objects | 2.10% |
| mAP — medium objects | 21.55% |
| mAP — large objects | 28.42% |
| AR @ 100 proposals | 10.37% |

**Inference Animation**: [`resnet/data/animation.gif`](resnet/data/animation.gif)

---

### Experiment 3 — EfficientDet D1 (SSD EfficientNet-B1 BiFPN 640×640)

| Parameter | Value |
|---|---|
| Pre-trained checkpoint | `efficientdet_d1_coco17_tpu-32` |
| Feature extractor | `ssd_efficientnet-b1_bifpn_keras` (BiFPN, 4 iterations, 88 filters) |
| Training steps | 2,000 |
| Batch size | 8 |
| Instance | ml.g5.xlarge |
| Optimizer | SGD + Momentum (0.9) |
| Learning rate | 0.08, cosine decay, warmup=2,500 steps |
| Augmentations | 7 strategies: `random_horizontal_flip`, `random_scale_crop_and_pad_to_square`, `random_adjust_brightness`, `random_adjust_contrast`, `random_adjust_saturation`, `random_adjust_hue`, `random_jpeg_quality` |

**Training Loss Progression**

| Step | Total Loss |
|---|---|
| ~100  | 0.573 |
| ~200  | 0.366 |
| ~300  | 0.350 |
| ~400  | 0.321 |
| ~500  | 0.337 |
| ~2,000 | ~0.31 |

> **Note:** EfficientDet's training loss is not directly comparable to MobileNet/ResNet values — the loss function (focal + box regression) is architecturally different and uses a different scale. Evaluation metrics (mAP) were not captured in the notebook output; they would be visible in TensorBoard or by running the model evaluation script separately. The training run completed, and inference was deployed successfully (see animation below).

**Inference Animation**: [`efficientnet/data/animation.gif`](efficientnet/data/animation.gif)

---

## Results Summary

| Model | Steps | Final Train Loss | mAP (0.50–0.95) | mAP@0.50 | AR@100 |
|---|---|---|---|---|---|
| SSD MobileNet v2 FPNLite | 2,000 | ~0.68 | **10.31%** | **22.00%** | **16.00%** |
| SSD ResNet50 v1 FPN | 2,000 | ~0.87 | 6.32% | 12.04% | 10.37% |
| EfficientDet D1 | 2,000 | ~0.31 | N/A* | N/A* | N/A* |

> *EfficientDet D1 evaluation metrics were not captured in notebook output. Loss values are not cross-comparable across architectures.

---

## Analysis

### Training Loss vs. Validation Loss

The TF Object Detection API does not output a scalar "validation loss" — instead it reports COCO detection metrics (mAP, AR) on the validation set at the final checkpoint. Training loss is the only loss curve available during training.

Both MobileNet and ResNet showed:
- A **declining training loss** curve from start to step 2,000, confirming the models were actively learning.
- A **significant gap** between the lower training loss and the relatively low mAP on the validation set.

This gap indicates **underfitting**: both models were still far from convergence at 2,000 steps. The validation mAP being much lower than what the training loss would suggest (for a fully trained model) is expected — the models have not yet learned to generalise the patterns to unseen data.

For ResNet specifically, the training loss decreased more slowly and remained higher (~0.87 vs ~0.68 for MobileNet). A key reason is a **misconfigured learning rate warmup**: `warmup_steps` was set to 2,000, matching the total training steps budget. This means the learning rate was still in its warmup phase for the entire run and never reached its base value of 0.04 — the model was effectively training with a sub-optimal, sub-base learning rate throughout.

EfficientDet achieved visually lower training loss (~0.31), but this is not directly comparable since EfficientDet uses a focal loss (for classification) combined with a box regression loss at a different scale. Its richer augmentation strategy (7 options vs 2) likely helped regularise training, though the short 2,000-step run was also within its warmup schedule.

### Did You Expect This Behavior?

Yes. This behavior is entirely expected for the following reasons:

1. **Insufficient training steps**: All three models are designed to train for 25,000–300,000 steps. Running only 2,000 steps is equivalent to a very early snapshot — the models are still adapting from COCO-pretrained weights to the Waymo urban domain.

2. **Domain gap**: Models were pre-trained on COCO and fine-tuned on Waymo data. The urban autonomous-driving scenes in Waymo differ from generic COCO images (dense traffic, viewpoint angles, class imbalance toward vehicles).

3. **Warmup phase effects**: Early training steps are dominated by learning-rate warmup, during which weights change slowly. 2,000 steps barely exits the warmup period for these models.

4. **Class imbalance**: The Waymo dataset has far more Vehicles than Pedestrians or Cyclists, making it harder to detect the minority classes, which pull down overall mAP.

The strong performance on large objects (MobileNet mAP large = 53.2%) compared to small objects (4.5%) is also expected: at 640×640 input resolution, small pedestrians and distant cyclists may occupy only a few pixels, making them hard to detect without many training examples and fine-grained feature learning.

---

## Recommended Model: SSD MobileNet v2 FPNLite 640×640

**MobileNet v2 FPNLite is the best model** for this use case among the three experiments, for the following reasons:

1. **Highest mAP**: Achieved 10.31% mAP (IoU 0.50–0.95) and 22.0% mAP@50 — **63% higher** than SSD ResNet50 at the same 2,000-step budget.
2. **Faster convergence**: Training loss dropped from 0.99 → 0.68 cleanly, showing the model made good progress within the available budget.
3. **Better calibrated LR schedule**: The warmup ended at step 1,000, allowing 1,000 steps of full-LR training — unlike ResNet which never exited warmup.
4. **Efficiency for AV deployment**: MobileNet v2 is a lightweight backbone designed for real-time inference on embedded hardware. For autonomous driving, latency and throughput matter as much as accuracy.
5. **Better recall**: AR@100 of 16.0% vs. ResNet's 10.4%, meaning MobileNet generates better candidate proposals across IoU thresholds.

EfficientDet D1 is architecturally superior with its BiFPN neck and richer augmentation strategy, and its lower training loss is promising. However, without comparable evaluation metrics, it cannot be ranked directly against the others in this experiment set.

---

## How to Further Improve Performance

### 1. Increase Training Steps Significantly
The single highest-impact change. MobileNet and ResNet are designed for 50,000–300,000 steps. At minimum, train for **25,000** steps to see meaningful gains:

```
"num_train_steps": "25000"
```

### 2. Enrich Data Augmentation
Add photometric and geometric augmentations to improve generalisation to diverse lighting and weather conditions (common in urban driving scenes):

```protobuf
data_augmentation_options { random_adjust_brightness { max_delta: 0.3 } }
data_augmentation_options { random_adjust_contrast { min_delta: 0.7; max_delta: 1.3 } }
data_augmentation_options { random_adjust_saturation { min_delta: 0.7; max_delta: 1.3 } }
data_augmentation_options { random_adjust_hue { max_delta: 0.02 } }
data_augmentation_options { random_jpeg_quality { min_jpeg_quality: 50; max_jpeg_quality: 100 } }
data_augmentation_options { random_black_patches {} }
```

### 3. Fix the ResNet Warmup Configuration
Reduce `warmup_steps` from 2,000 to a fraction of the total steps (e.g., 10%):

```protobuf
warmup_learning_rate: .013333
warmup_steps: 2500  # for a 25,000-step run
```

### 4. Learning Rate Tuning
For MobileNet, experiment with higher base LR (0.1–0.2) if training longer, since short runs benefit from aggressive early updates.

### 5. Add Per-Class Evaluation
The current pipeline reports only overall mAP. Instrument per-class metrics (Vehicle, Pedestrian, Cyclist) to understand which classes underperform and apply class-weighted sampling if needed.

### 6. Consider Larger Input Resolution
For detecting small pedestrians and cyclists, increasing the input from 640×640 to **1024×1024** significantly improves small-object mAP, at the cost of training speed.

### 7. Train EfficientDet D1 Longer with Evaluation
EfficientDet showed the lowest training loss and the richest augmentation pipeline. Training it for 25,000+ steps and capturing evaluation metrics would likely reveal it as the best performer given its BiFPN multi-scale feature aggregation.
