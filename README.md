# REAL-TIME GAME ANTI-ALIASING TECHNIQUES USING DEEP NEURAL NETWORKS

<p align="center">
  <img src="TAA_MSAA_comparativa.gif" alt="Comparison between TAA and MSAA." width="800"/>
</p>

The main objective of this project is to research, analyze, and develop deep neural network-based anti-aliasing techniques for application in video games. Multiple models were developed using different architectures such as CNN, UNet, and Transformer. These models not only aim to correct ghosting but also address other common visual issues, including jagged edges, image sharpness enhancement, and the removal of various rendering artifacts.  

To train and evaluate the models, an extensive dataset of images was collected from custom-designed scenes in the Unreal Engine graphics engine. These images were preprocessed to serve as input for the models, which output enhanced versions with applied anti-aliasing and noticeably superior visual quality.

<div align="center">

| TAA (with ghosting) |
|----------------------|
| <img src="TAA_antialiasing_example.gif" width="800"/> |

| MSAA (ground truth) |
|---------------------|
| <img src="MSAA_antialiasing_example.gif" width="800"/> |

</div>

---

## Methodology

For the development of the project, an **agile Scrum methodology** was followed, with sprints lasting one to two weeks.  

The workflow was structured into the following steps:

1. **Dataset Creation**  
   A virtual environment was designed and developed in **Unreal Engine 5** to generate a synthetic dataset.  
   Sequences were recorded at **1920x1080p and 60 FPS**, capturing images with **TAA** (used as model input) and with **MSAA** (ground truth or high-quality reference).

2. **Model Training**  
   Several neural network architectures were trained and validated using this dataset.  
   Intensive training was carried out on the **Picasso supercomputer**.

3. **Results Evaluation**  
   The models’ performance was compared both quantitatively and qualitatively, focusing on metrics such as **PSNR** and the reduction of **ghosting** and other artifacts.

---

## Architectures Used

The following architectures, specialized in video and image restoration and super-resolution, were trained and evaluated:

- **EDVR (Enhanced Deformable Video Restoration):** a powerful network for video restoration, leveraging multi-frame alignment and attention mechanisms.  
- **BasicVSR++:** an architecture based on bidirectional feature propagation.  
- **VRT (Video Restoration Transformer):** employs *Transformers* to capture spatial and temporal dependencies.  
- **DRUNet (Deep Residual U-Net):** combines *U-Net* and *ResNet* principles for image denoising and restoration.  
- **NAFNet (Nonlinear Activation Free Network):** an innovative network that achieves state-of-the-art performance without nonlinear activation functions.

---

## Results

The results were evaluated using **PSNR (Peak Signal-to-Noise Ratio)**, a standard metric for measuring reconstruction quality.  

<div align="center">

| Scene              | VRT   | EDVR  | BasicVSR++ | DRUNet | NAFNet |
|--------------------|-------|-------|------------|--------|--------|
| Scene 1 - Bench    | 23.89 | 25.00 | 16.70      | 23.14  | 26.16  |
| Scene 2 - Tree     | 20.57 | 20.40 | 20.55      | 23.15  | 25.44  |
| Scene 3 - Ferns    | 23.21 | 23.13 | 19.46      | 25.26  | 26.30  |
| Scene 4 - Lake     | 25.05 | 24.50 | 21.24      | 24.98  | 22.75  |
| Scene 5 - Arch 1   | 25.65 | 26.06 | 19.73      | 24.41  | 25.52  |
| Scene 6 - Arch 2   | 25.86 | 25.43 | 20.08      | 24.63  | 25.47  |
| Scene 7 - Overlook | 26.68 | 26.49 | 21.65      | 27.02  | 26.54  |

</div>

**Results Analysis:**  
- **NAFNet** stood out by achieving the best results in most scenes, particularly on transparent surfaces.  
- **EDVR** showed excellent capacity for removing aliasing and ghosting.  
- **VRT** excelled in the sharpness of its reconstructions.  
- **DRUNet** delivered acceptable performance, though without major perceptual improvements.  
- **BasicVSR++** performed the worst, occasionally degrading the quality of the input image.  

---

## Installation Guide

### System Requirements
- **OS:** Linux (also supported on Windows via WSL or Docker).  
- **Python:** Recommended Python 3.7 – 3.10 (virtual environments with Anaconda or Miniconda are recommended).  
- **PyTorch:** Version 1.10 with CUDA support.  
- **GPU:** NVIDIA with CUDA support (**at least 12 GB VRAM** recommended for training).  

---

## Installation 

All source code required to run and reproduce this project is organized in the **TFG_AntiAliasing** folder. This folder can be downloaded from the following <a href="https://drive.google.com/drive/folders/1nkHAZJ5TlYn7uwUizH8rhuJjfjGtI4VX">link</a>.

### Using Miniconda or Anaconda:
```bash
conda create -n environment_name python=3.9
conda activate environment_name
```
### **IMPORTANT:** It is recommended to create a separate environment for BasicSR, KAIR, and NAFNet.

## For installing the dependencies required for the different models, refer to the document “TFG_Antialiasing”, section “Installation Guide”.
## For training, validation, and inference, refer to the document “TFG_Antialiasing”, section “User Manual”.
