# Semantic Segmentation in Orthomosaics
This repository contains the implementation and experiments conducted for the segmentation of Araucaria tree crowns using Convolutional Neural Networks (CNNs). The project compares the performance of the **U-Net**, **SegNet** and **DeepLabv3+** architectures across different data scenarios.

## 📌 Project Overview
The objective of this work is to identify and map specimens of Araucaria angustifolia in high-resolution aerial images captured by drones. The methodology ranges from orthomosaic preprocessing (image splitting) to the statistical validation of the trained models.

### Evaluated Architectures:
* **U-Net:** Focus on edge precision via skip connections.
* **SegNet:** Efficient architecture based on pooling indices.
* **DeepLabv3+:** Multi-scale segmentation with atrous convolutions (ASPP).

---

## 🛠️ Technologies and Libraries
The project was developed in Python 3.13.6 and the following libraries are required:

* **[PyTorch](https://pytorch.org/):** Main framework for building and training the networks.
* **[Torchvision](https://pytorch.org/vision/stable/index.html):** Application of Data Augmentation and vision utilities.
* **[NumPy](https://numpy.org/):** Matrix and tensor manipulation.
* **[Scikit-Learn](https://scikit-learn.org/):** Splitting of train/validation/test datasets.
* **[Matplotlib](https://matplotlib.org/):** Graph generation and mask visualization.
* **[SciPy](https://scipy.org/):** Execution of the Wilcoxon Statistical Test.
* **[Pillow (PIL)](https://python-pillow.org/):** Basic image processing.

---

## 🚀 How to Run the Code

### 1. Hardware and Environment Requirements
The use of an NVIDIA GPU is strongly recommended to accelerate training, due to the high computational cost of convolutional networks (especially U-Net and DeepLabv3+).

* **`Local`**: Make sure to install the PyTorch version compatible with your CUDA Toolkit version.

* **`Cloud`**: If using Google Colab or similar platforms, remember to change the runtime environment to "GPU" before running the scripts.

### 2. Dataset Organization
Before running the codes, it is necessary to consolidate the images into the correct folder structure. In the same root directory as the code files, create the following hierarchy:

```text
📁 project_root/
├── 📁 tiles/
│   ├── 📁 image/  <-- (Merge all images extracted from "image_part1" and "image_part2" here)
│   └── 📁 mask/   <-- (Add all corresponding masks here)
├── 📓 Unet_Original_Filtrado.ipynb
└── ...
```
Explanatory note: As the original volume of images is high, the files were divided into two parts (image_part1 and image_part2). You must extract the contents of both and merge everything inside the tiles/image/ folder.

### 3. 3. Test Configuration and Execution
The experiments were structured in Jupyter Notebook format. To execute the trainings, open the notebook of the desired network and navigate to the last code block.

There you will find the global variables that control the execution. You can adjust them according to your testing needs:

* **`seeds`**: Defines the random initialization seeds (e.g., 16, 32, 64, 128) to ensure reproducibility.
* **`num_rodadas`**: Amount of independent runs that will be executed for each seed.
* **`cenario`**: Defines which data approach will be used (Original, Filtered, or Augmentation).
* **`arquivo_saida`**: Defines the name of the log file (`.csv`) where the metrics (Time, IoU, F1-Score, Epochs) will be saved.

After configuring these parameters, simply execute all the cells in the notebook sequentially.
