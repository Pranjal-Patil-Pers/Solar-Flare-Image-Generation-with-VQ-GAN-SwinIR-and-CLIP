# Solar Flare Image Generation with VQ-GAN, SwinIR Super Resolution, and CLIP Extension

CSC 8851 Deep Learning project (Fall 2025), Georgia State University.

This project investigates how modern generative and restoration models can be
used to synthesize and enhance solar flare magnetograms. We train a VQ-GAN on
SHARP active region patches to learn a compact latent representation, use
SwinIR to recover high resolution structure from low resolution inputs, and
explore CLIP as a way to relate text descriptions of solar activity to
generated images. Together, these components provide a modular workflow for
flare image generation, super resolution, and qualitative evaluation.

## Dataset

We use SHARP line of sight magnetograms from the HMI instrument on SDO
(May 2010 to 2018, one hour cadence). The data consists of 512x512 active
region patches with associated flare labels based on the next 24 hour peak
GOES X ray flux.

Dataset link:  
https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/WLTBQQ

You need to download the dataset separately and adjust the paths near the
top of each notebook to point to your local copy or your Google Drive paths.

## Repository structure

- `vqgan/`  
  - `VQ_model_1_9_training.ipynb`  
    Trains a VQ-GAN on 256x256 SHARP magnetogram crops. Includes data
    loading, model definition, training loops, and logging of reconstruction
    quality for flare and non flare patches.

- `super_resolution/`  
  - `1_sharp_swinir_training.ipynb`  
    Trains a SwinIR based 2x super resolution model on paired low resolution
    and high resolution SHARP patches, and reports PSNR and SSIM on a held
    out test set.
  - `2_swinir_on_generated_images.ipynb`  
    Loads the trained SwinIR checkpoint and applies it to VQ-GAN generated
    flare and non flare magnetograms, producing 512x512 super resolved
    versions and saving the figures used in the report.

- `clip_guidance/`  
  - `Clip_guidance.ipynb`  
    Runs CLIP based experiments using a pretrained CLIP model. Sets up text
    prompts, computes text image similarity scores for VQ-GAN generated
    images, and explores CLIP plus VQ-GAN text to image optimization.

## Running the notebooks

The notebooks were developed in Google Colab.

1. Open the desired notebook in Colab.
2. Mount your Google Drive if needed and edit the data paths at the top of the
   notebook so they point to your SHARP dataset and model checkpoints.
3. Install any missing Python packages using the `pip install` commands
   provided in the first cells.
4. Run all cells in order to reproduce the training runs and figures.

## Team

- Benedict Antonio Mervyn  
- Pranjal Patil  
- Shreya Gaikwad
