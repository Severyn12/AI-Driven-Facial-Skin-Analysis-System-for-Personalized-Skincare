# AI-Driven-Facial-Skin-Analysis-System-for-Personalized-Skincare

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
│   └── experiments/        # notebooks for acne segmentation experiments
├── wrinkles/
│   └── experiments/        # notebooks for wrinkle segmentation experiments
├── skin_evenness/
│   ├── experiments/        # notebooks for tone and texture evenness analysis
│   ├── utils/              # MediaPipe FaceMesh landmarks and helper utilities
│   ├── models/             # MediaPipe FaceMesh model
│   └── results/            # calculated tone and texture evenness scores for FFHQ-Wrinkle dataset
├── preprocess/             # CLAHE conditioned on ITA preprocessing experiments
├── overall_skin_assesment.ipynb          # overall facial skin assessment pipeline
```

The `experiments/` folders contain Jupyter notebooks with the implementation of experiments for each facial feature.

For the skin evenness analysis, the `utils/` folder additionally contains MediaPipe FaceMesh landmarks used for facial ROI extraction, while the `models/` folder stores the MediaPipe FaceMesh model itself.

The `results/` folder contains precomputed tone and texture evenness scores for individuals from the FFHQ-Wrinkle dataset.

The `preprocess/` folder contains notebooks related to preprocessing experiments, including the implementation of the CLAHE transformation conditioned on ITA, which is used to enhance contrast under varying illumination and skin tone conditions.

The `overall_skin_assesment.ipynb` notebook combines all developed approaches into one pipeline and computes the final aggregated facial skin assessment score.

---

## Models

The best-performing models for both acne segmentation and wrinkle detection are available on Google Drive:

- Acne segmentation model: [Google Drive Link](https://drive.google.com/file/d/1JpJ_yMaXxowaJpTBC1lgN54_PWeubrFR/view?usp=sharing)
- Wrinkle segmentation model: [Google Drive Link](https://drive.google.com/file/d/1vjOU7pGVKFKyd7Ui122RYa8NrsQdcOYj/view?usp=sharing)

These checkpoints correspond to the final versions used in the thesis experiments.

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
