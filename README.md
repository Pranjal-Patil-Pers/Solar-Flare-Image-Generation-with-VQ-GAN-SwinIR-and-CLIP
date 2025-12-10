# Solar Flare Image Generation with VQ-GAN, SwinIR Super Resolution, and CLIP Extension

Course project for CSC 8851 (Fall 2025), Georgia State University.

This repository contains code and notebooks for generating and analyzing solar
flare magnetograms using VQ-GAN, SwinIR based super resolution, and a CLIP
based extension for semantic guidance and evaluation.

## Dataset

We use SHARP line of sight magnetograms from the HMI instrument on SDO
(May 2010 to 2018, one hour cadence), provided as 512×512 active region patches
with associated flare labels.

Dataset link:  
https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/WLTBQQ

## Repository structure

- `vqgan/`  
  VQ-GAN training, reconstruction, and sampling notebooks for low resolution
  flare and non flare magnetograms.

- `super_resolution/`  
  SwinIR super resolution notebooks that train on SHARP magnetograms and
  upscale VQ-GAN generated images.

- `clip_guidance/`  
  CLIP based experiments for text image similarity and optional guided sampling.


## Team

- Benedict Antonio Mervyn  
- Pranjal Patil  
- Shreya Gaikwad
