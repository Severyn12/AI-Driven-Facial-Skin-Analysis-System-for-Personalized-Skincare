# AI-Driven-Facial-Skin-Analysis-System-for-Personalized-Skincare

# AI-Driven Facial Skin Analysis System for Personalized Skincare

##
This repository contains the implementation of experiments for the thesis:

**"AI-Driven Facial Skin Analysis System for Personalized Skincare"**

The main goal of this work is to investigate how different preprocessing strategies affect robustness to lighting conditions and skin tone variations in facial skin analysis tasks.

The system focuses on:
- Acne segmentation
- Wrinkle detection
- Skin tone and texture evenness estimation

Additionally, a multi-model pipeline is developed to compute an **aggregated skin condition score**.

---

## Key Contributions

- Comparative analysis of preprocessing strategies:
  - Augmentations (lighting simulation)
  - Facial ROI extraction
  - CLAHE conditioned on ITA

- Evaluation of feature-specific behavior:
  - CLAHE improves wrinkle detection
  - CLAHE degrades acne detection (noise + color distortion)

- Development of an **aggregated skin score**
- Exploration of **CLIPSeg** for prompt-based acne segmentation

---

## Project Structure 

```text
.
├── acne/
│   ├── models/
│   └── experiments/
├── wrinkles/
│   ├── models/
│   └── experiments/
├── evenness/
│   └── experiments/
```


---

## Datasets

### Wrinkle Analysis
- **FFHQ-Wrinkle Dataset**
- High-resolution images (1024×1024)
- Includes:
  - Manually annotated wrinkle masks
  - Weak labels (texture maps)
- Diverse conditions (lighting, pose, ethnicity)
- The dataset was published on [Kaggle](https://www.kaggle.com/datasets/karmagames/wrinkles-dataset)

---

### Acne Analysis
- **ACNE04-v2 (main dataset)**
  - ~1200 images
  - Circular annotations (improved over bounding boxes)
  - Higher-quality labels
  - The dataset was published on [Kaggle](https://www.kaggle.com/datasets/karmagames/acne04-v2)


- **Acne Dataset (Kaggle, auxiliary)**
  - Used for semi-supervised experiments
  - Diverse skin conditions and ethnicities
  - The dataset was published on [Kaggle](https://www.kaggle.com/datasets/tiswan14/acne-dataset-image)

---

### Evenness Analysis
- No suitable public dataset available

Synthetic data was generated:
- Texture: Gaussian smoothing
- Tone: CIELAB a-channel distortion
