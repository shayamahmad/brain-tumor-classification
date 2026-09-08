# Brain Tumor MRI Classification - CNN-GNN Framework

This repository contains the code and notebooks accompanying the manuscript:

**"An Explainable Spatial-Relational Graph Learning Framework for Accurate Brain Tumor Classification from MRI"**

## Dataset

This study uses the **Brain Tumor MRI Dataset**, publicly available on Kaggle:

🔗 **[https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)** (see version note below)

> **⚠️ Note on dataset version:** The experiments in this study were conducted using **Version 1** of this dataset, which contained **7,023 images**:
> 🔗 **[https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset/versions/1](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset/versions/1)**
>
> The dataset has since been updated to **Version 2**, which contains **7,200 images**. If you are attempting to reproduce our exact results, please use the **Version 1** link above (7,023 images: 2,000 no-tumor, 1,757 pituitary, 1,645 meningioma, 1,621 glioma). Using the current Version 2 will not exactly reproduce our reported figures, since the underlying sample counts differ.

This dataset is a curated combination of three publicly available brain tumor MRI sources:

- **Figshare Brain Tumor Dataset** ([Cheng, 2017](https://doi.org/10.6084/m9.figshare.1512427.v8))
- **SARTAJ Brain Tumor Classification (MRI)** ([Kaggle](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri))
- **Br35H: Brain Tumor Detection 2020** ([Kaggle](https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection))

### Known data curation note (from the dataset creator)

The "no tumor" class images were taken from the Br35H dataset. The dataset creator identified that the **SARTAJ dataset's glioma class images were mislabeled** (confirmed both by the creator's own model results and by other users' independent findings), and therefore **replaced the SARTAJ glioma images with the corresponding Figshare glioma images** in this combined dataset. This is the documented source of the "wrongly labeled samples...removed" step referenced in our manuscript's dataset preparation description.

Image dimensions vary across the combined dataset (inherited from the three source datasets), which is why resizing/normalization is applied during preprocessing, as described in our manuscript (Section 3.2).

### Classes and sample counts

| Class | Number of Images |
|---|---|
| No Tumor | 2,000 |
| Pituitary | 1,757 |
| Meningioma | 1,645 |
| Glioma | 1,621 |
| **Total** | **7,023** |

### Data split

The dataset was split into training, validation, and testing subsets using an **80:10:10** ratio, stratified by class:

| Split | Samples |
|---|---|
| Train | 5,618 |
| Validation | 702 |
| Test | 703 |

## Usage

1. Download the dataset from the Kaggle link above (requires a free Kaggle account).
2. Place the extracted image folders according to the paths expected in the notebook(s) in this repository.
3. Run the notebook(s) to reproduce preprocessing, CNN feature extraction (ResNet50, InceptionV3, EfficientNet-B3), graph construction, GCN training, metaheuristic hyperparameter optimization (PSO, MFO, GWO), and explainability (Grad-CAM, Grad-CAM++, Score-CAM, GNNExplainer) as described in the manuscript .

## Citation

If you use this code or the associated dataset combination, please cite the original dataset sources above along with our manuscript (citation details to be added upon publication).

## License

Please refer to the individual licenses of the original dataset sources (Figshare, SARTAJ, Br35H) linked above for terms of use.
