# BirdSpectrogramSynthesis

This repo links the code used for my Masters project, as well as its results. Credit for the code adapted has been provided for each entry. Reproducibility of my results is hopefully improved by the sharing of code. My notebooks have been commented and organised to act also act as a guide to synthesising spectrograms of bird vocalisations using Stable Diffusion.

# Guide to generating your own Synthetic Bird Spectrograms:

## Step 1: Training Data Collection

Find audio recordings of the desired bird, Xeno-canto is an excellent resource. Ideally, a bird species with a specific vocalisation type (e.g. call) with 5-10 cleanly visible vocalisations is best. Within Xeno-canto, you can view the spectrograms for your search results, and look for these. Download the recordings that appear suitable.

Using the audio software Audacity, open your recordings and change the view to allow you to see their spectrograms. From them, manually crop out just the relevant audio (e.g. the call), making sure that each sample is of same length and noting this length down. For context, the Iiwi call was 0.50 seconds and the Sunbird call 0.75 seconds, both with 7 samples.

## Step 2: Training Data Pre-processing

Convert your audio samples into Mel spectrograms. The conversion parameters, specifically the mel hop_length, may have to be adjusted for different sample lengths as described in the notebook.

Code: https://colab.research.google.com/drive/1T19LLjZTZiuoXfGu9tiwyjybcjb8m5H5?usp=sharing

Credit for code adapted from repo https://github.com/teticio/audio-diffusion.

## Step 3: Fine-tune Riffusion via Dreambooth with LoRA, and Spectrogram inference

Using your training spectrograms, fine-tune the pretrained Riffusion model so that new images can be generated as desired.

Code: https://colab.research.google.com/drive/1uYm_NQy7vUvqmHM2xgMOjuvYPxuJv7yZ#scrollTo=EZH8PmZoncOj

Adapted code. Original notebook at https://colab.research.google.com/drive/1iSFDpRBKEWr2HLlz243rbym3J2X95kcy?usp=sharing, credit to pedrogengo (https://github.com/pedrogengo). Original LoRA repo to cloneofsimo (https://github.com/cloneofsimo/lora).

## Step 4: Invert generated spectrograms to audio

The following notebook allows the inversion of spectrograms (both real and synthetic) into audio files via the Griffin-Lim Algorithm. It will inverse all the spectrogram images in a directory into audio files.

Code: https://colab.research.google.com/drive/1dMI8t8eZLEA9uq4fS1VpvdAMv8D_k2u1?usp=sharing

Credit to teticio for the original codebase https://github.com/teticio/audio-diffusion.

## Step 5: Evaluation of Synthetic Spectrograms. 

The code to compute power spectra density plots can be found at: <br>
Todo---

The code to compute and plot pairwise multiscale structural similarity (MS-SSIM): <br>
Todo---

# Diffusion Model Literature Search 

This notebook will search arxiv for 
(diffusion model OR diffusion models OR diffusion) AND (image OR vision OR text-to-image OR text to image).
It also will check the references in the papers found from arxiv, and append any that meet the search criteria, using semantic scholar. 
The results from these searches have been uploaded to this repo within the results_csv files.

Code: https://colab.research.google.com/drive/1YE5r5IOf5hLvqcAHhKJSVl44nNUUG68h?usp=sharing

Credit to arkel123, https://github.com/arkel23/literatureReview_arxivSemanticScholarManual, and the creators of the wrappers for the arXiv and Semantic Scholar APIs:
https://github.com/lukasschwab/arxiv.py, https://github.com/danielnsilva/semanticscholar.

