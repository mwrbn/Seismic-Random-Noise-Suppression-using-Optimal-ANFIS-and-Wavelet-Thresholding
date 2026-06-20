# Seismic Random Noise Suppression using Optimal ANFIS and Wavelet Thresholding (OANFIS-WT)

## Overview

This repository implements a hybrid seismic signal denoising framework based on **Optimal Adaptive Neuro-Fuzzy Inference System (OANFIS)** and **Wavelet Thresholding (WT)** for suppressing random noise in seismic records.

Traditional filtering methods often struggle to preserve weak seismic events while removing broadband random noise. The proposed framework combines:

* Adaptive Neuro-Fuzzy Inference System (ANFIS)
* Honey Badger Algorithm (HBA) optimization
* Adaptive Self-Tuning Filtering
* Wavelet Thresholding (WT)
* Multi-level Discrete Wavelet Transform (DWT)

The combination provides robust noise attenuation while preserving important seismic reflections and amplitude information.

---

## Features

* Adaptive self-tuning seismic filtering
* HBA-optimized ANFIS parameters
* Wavelet-based residual noise removal
* Synthetic and real seismic data experiments
* Signal quality evaluation metrics
* Python implementation
* Modular structure
* Easy extension for new optimization algorithms

---

## Methodology

The proposed workflow consists of three stages:

### 1. Optimal ANFIS (OANFIS)

ANFIS acts as an adaptive self-tuning filter and extracts useful seismic information from noisy data.

Unlike conventional ANFIS, the premise and consequent parameters are optimized using the Honey Badger Algorithm (HBA), avoiding local minima problems.

---

### 2. Honey Badger Algorithm (HBA)

HBA optimizes:

* Premise parameters
* Consequent parameters

using Mean Squared Error (MSE) as the objective function.

Benefits:

* Fast convergence
* Improved global search capability
* Lower reconstruction error
* Better parameter estimation

---

### 3. Wavelet Thresholding

Residual noise remaining after OANFIS filtering is removed by:

* Discrete Wavelet Transform (DWT)
* Multi-level decomposition
* Improved thresholding function proposed by Li et al.
* Signal reconstruction

The repository uses:

* Symlet wavelet (sym11)
* Four-level decomposition

which provides the best denoising performance.

---

## Pipeline

```text
Noisy Seismic Signal
        │
        ▼
Adaptive Self-Tuning Filter (ANFIS)
        │
        ▼
Honey Badger Optimization
        │
        ▼
Optimal ANFIS (OANFIS)
        │
        ▼
Wavelet Decomposition
        │
        ▼
Thresholding Function
        │
        ▼
Signal Reconstruction
        │
        ▼
Denoised Seismic Signal
```

---

## Mathematical Models

### Gaussian Membership Function

```math
μ(x)=exp(-(x-c)^2/(2σ^2))
```

where:

* c : mean
* σ : standard deviation

---

### Rule Firing Strength

```math
ω_i = μ_P(x) × μ_Q(y)
```

---

### Normalized Firing Strength

```math
ω̄_i = ω_i /(ω_1+ω_2)
```

---

### ANFIS Output

```math
F_i = u_i x + v_i y + w_i
```

Final output:

```math
Output = Σ(ω̄_i F_i)
```

---

### Objective Function

```math
MSE = (1/N) Σ(t_i-y_i)^2
```

---

### Wavelet Thresholding Function

```math
ω̃ = ω - λ /(α(ω-λ)^β +1)
```

where:

* α : adjustment parameter
* β : shape parameter
* λ : threshold

---

## Performance Metrics

The algorithm is evaluated using:

### Signal-to-Noise Ratio (SNR)

```math
SNR = 10 log10(signal power/noise power)
```

### Mean Square Error (MSE)

```math
MSE = (1/N) Σ(s-ŝ)^2
```

### Root Mean Square Error (RMSE)

```math
RMSE = √MSE
```

### Percentage Root Difference (PRD)

```math
PRD = 100 × RMSE / signal energy
```

### Correlation Coefficient (CC)

Measures similarity between original and reconstructed signals.

---

## Repository Structure

```text
Seismic-Random-Noise-Suppression-OANFIS-WT
│
├── README.md
├── requirements.txt
├── main.py
├── config.py
│
├── data
│   ├── synthetic
│   └── real
│
├── models
│   ├── anfis_model.py
│   ├── hba_optimizer.py
│   ├── wavelet_threshold.py
│   └── membership_functions.py
│
├── metrics
│   ├── mse.py
│   ├── rmse.py
│   ├── snr.py
│   ├── prd.py
│   └── cc.py
│
├── figures
│   ├── convergence_curve.png
│   ├── membership_function.png
│   ├── threshold_function.png
│   ├── synthetic_results.png
│   └── real_results.png
│
├── notebooks
│   └── experiments.ipynb
│
├── results
│   ├── synthetic
│   └── real
│
└── paper
    └── original_paper.pdf
```

---

## Installation

Clone the repository

```bash
git clone https://github.com/username/Seismic-Random-Noise-Suppression-OANFIS-WT.git

cd Seismic-Random-Noise-Suppression-OANFIS-WT
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## Requirements

```txt
numpy
scipy
matplotlib
pywavelets
scikit-fuzzy
scikit-learn
pandas
```

---

## Usage

Run the main program

```bash
python main.py
```

Example

```python
from models.anfis_model import OANFIS
from models.wavelet_threshold import wavelet_denoise

signal = load_data()

filtered_signal = OANFIS(signal)

denoised_signal = wavelet_denoise(filtered_signal)
```

---

## Experimental Results

The proposed OANFIS-WT framework demonstrates:

### Synthetic Signals

* Higher SNR
* Lower MSE
* Better signal reconstruction

Compared with:

* EMD-DWT
* VMD-DWT

---

### Real Seismic Signals

The method preserves:

* Reflection amplitudes
* Weak seismic events
* Structural continuity

while effectively suppressing broadband random noise.

---

## Advantages

✔ Adaptive self-tuning filter

✔ No prior knowledge of noise required

✔ HBA prevents local minima

✔ High convergence speed

✔ Effective residual noise removal

✔ Preserves seismic events

✔ Modular Python implementation

✔ Easy to extend

---

## Future Work

Possible improvements include:

* Deep learning-based ANFIS
* PSO, GWO, and WOA optimization
* CEEMDAN decomposition
* VMD integration
* Transformer models for seismic denoising
* GPU acceleration
* Real-time seismic processing
* 2D and 3D seismic volume denoising

---

## Citation

If you use this repository in your research, please cite:

Geetha, K., & Hota, M. K.

**"Seismic Random Noise Suppression using Optimal ANFIS as an Adaptive Self-tuning Filter and Wavelet Thresholding."**

IEEE Access, 2024.

---

## Authors

**K. Geetha**

Department of Communication Engineering

Vellore Institute of Technology

India

---

**Malaya Kumar Hota**

Professor

Department of Communication Engineering

Vellore Institute of Technology

India

---

## License

This project is intended for research and educational purposes.

---

## Keywords

Seismic Signal Processing • Random Noise Attenuation • ANFIS • OANFIS • Honey Badger Algorithm • Wavelet Thresholding • Adaptive Filtering • Signal Denoising • HBA • DWT • Seismic Exploration • Geophysics
