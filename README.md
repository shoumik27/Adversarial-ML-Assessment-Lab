# 🛡️ Adversarial ML Assessment Lab

> Real world evaluation of CNN robustness against adversarial attacks on CIFAR-10 with attack implementation, defense training, and full result analysis.

---

## Overview

This lab implements and evaluates **adversarial attacks against Convolutional Neural Networks** trained on CIFAR-10. It covers the full attack defense cycle: training a baseline CNN, mounting FGSM attacks at varying perturbation strengths, applying adversarial training as a defense, and measuring the accuracy delta. Results are logged as JSON and visualized as training curves.

---

## Key Results

| Metric | Value |
|---|---|
| Baseline Model Accuracy | **75%** |
| FGSM Attack Success Rate (ε=0.3) | **93.75%** |
| Adversarial Training Improvement | **+22.5%** |
| Dataset | CIFAR-10 |
| Attack Framework | Foolbox |

---

## Attack & Defense Pipeline

```
CIFAR-10 Dataset
      │
      ▼
 Train Baseline CNN (ResNet)
      │
      ├──► FGSM Attack (ε = 0.1, 0.2, 0.3) ──► Measure Accuracy Drop
      │
      ├──► PGD Attack ──► Measure Accuracy Drop
      │
      └──► Adversarial Training Defense ──► Evaluate Robustness Gain
```

---

## Attacks Implemented

| Attack | Type | Key Parameter |
|---|---|---|
| FGSM (Fast Gradient Sign Method) | White-box, single-step | ε (perturbation budget) |
| PGD (Projected Gradient Descent) | White-box, iterative | Steps, step size |
| CW (Carlini & Wagner) | Optimization-based | Confidence |

---

## Project Structure

```
Adversarial-ML-Assessment-Lab/
├── Adversial_ML_Lab.ipynb       # Main notebook — attacks, defenses, analysis
├── baseline_model.pt            # Trained baseline CNN weights
├── attack_results.json          # Per-attack accuracy results
├── defense_results.json         # Post-adversarial-training results
├── adversarial_analysis.png     # Accuracy vs. perturbation strength plots
├── training_curves.png          # Training and defense curves
├── REPORT.md                    # Full written analysis and findings
└── README.md
```

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep_Learning-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![Foolbox](https://img.shields.io/badge/Foolbox-Adversarial_Attacks-black?style=flat)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=flat)

---

## Getting Started

**Option 1 — Google Colab (recommended):**

1. Open `Adversial_ML_Lab.ipynb` in Google Colab
2. Set Runtime → Change runtime type → **GPU**
3. Run all cells sequentially

**Option 2 — Local:**

```bash
git clone https://github.com/shoumik27/Adversarial-ML-Assessment-Lab.git
cd Adversarial-ML-Assessment-Lab
pip install torch torchvision foolbox numpy matplotlib
jupyter notebook Adversial_ML_Lab.ipynb
```

---

## Key Findings

See [`REPORT.md`](./REPORT.md) for the full written analysis, including per attack breakdown, defense evaluation methodology, and recommendations for improving CNN robustness in production.

**TL;DR:** Standard CNNs are highly vulnerable to even simple single step attacks like FGSM at moderate perturbation strengths. Adversarial training significantly narrows this gap but introduces a clean accuracy trade off that must be managed carefully in real deployments.

---

## Author

**Shoumik Chandra** — AI Security Researcher
[GitHub](https://github.com/shoumik27)
