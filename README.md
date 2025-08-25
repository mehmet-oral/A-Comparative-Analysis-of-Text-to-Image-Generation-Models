Project Title: A Comparative Analysis of Text-to-Image Generation Models

Authors: Emirhan Tekez, Ahmet Arda Kocabag, Berkay Altmtas, Ozan Cem Bas, Mehmet Oral

Date: January 10, 2025

Overview
This project conducts a comprehensive performance evaluation of five pre-trained Text-to-Image (T2I) Generative Adversarial Network (GAN) models: DF-GAN, AttnGAN, AttnGAN+CL, DM-GAN, and DM-GAN+CL. The models are compared based on quantitative metrics (FID score, VRAM usage, inference time) and qualitative analysis of generated images.

Key Findings
*   DF-GAN achieved the best FID score (15.47) and fastest inference time (0.024s per image) but consumed the most VRAM (5623 MB).
*   Contrastive Learning (CL) consistently improved image quality. AttnGAN+CL and DM-GAN+CL outperformed their standard versions.
*   A clear trade-off exists between image quality (FID), computational cost (VRAM), and inference speed.
*   All models struggled with generating coherent human figures and multiple distinct objects.

Evaluated Models
1.  DF-GAN: A single-stage GAN with deep text-image fusion.
2.  AttnGAN: Uses word-level attention and a multi-stage generation process.
3.  AttnGAN+CL: AttnGAN enhanced with Contrastive Learning.
4.  DM-GAN: Employs a dynamic memory module for image refinement.
5.  DM-GAN+CL: DM-GAN enhanced with Contrastive Learning.

Evaluation Metrics
*   Frechet Inception Distance (FID): Lower is better. Measures realism and diversity of generated images.
*   VRAM Usage: Peak memory consumption during inference.
*   Inference Time: Time required to generate a single image.

Requirements
*   OS: Linux (Tested on Ubuntu 20.04)
*   GPU: NVIDIA GPU with CUDA 12.6
*   Python Packages: torch==1.9.0, torchvision==0.10.0, scikit-image==0.18.0, scipy==1.1.0, and others in the `requirements.txt` of each model.

Usage
The provided `Text2Image.py` script automates the entire evaluation process. It generates a Bash script (`term_proj.sh`) that:
1.  Clones all necessary model repositories from GitHub.
2.  Installs Python dependencies for DF-GAN.
3.  Runs the inference and FID calculation code for each model.

To execute the full evaluation pipeline:
`python Text2Image.py`

Project Structure
The script will create the following directory structure by cloning the respective repositories:
*   `DF-GAN/`
*   `AttnGAN/`
*   `DM-GAN/`
*   `T2I_CL/` (Contains AttnGAN+CL and DM-GAN+CL)

Results, including generated images and FID scores, will be saved within each model's directory according to their specific implementation.

Notes
*   The paths in the evaluation commands are hardcoded for a specific user directory (`/home/emirhan/`). These must be modified in the script to match your own environment before running.
*   The process is computationally intensive and requires a significant amount of VRAM and time to complete, especially for generating over 20,000 images per model.
*   Pre-trained model weights are automatically downloaded from Google Drive by the respective codebases.
