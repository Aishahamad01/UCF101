# UCF101
---

# 🧠📹 Video Generation Using Neural ODE

*Modeling Continuous Temporal Dynamics in Video Using Neural ODEs and ResNet Model*

---

## 🔍 Overview

This project explores a **neural ODE, ResNet and hybrid deep generative models** to generate realistic video clips. The model is trained on the **UCF101 action recognition dataset** and aims to model **continuous-time temporal dynamics** while maintaining **spatial resolution fidelity** in the generated frames.

We evaluate the approach using two standard video generation metrics:

* **SSIM (Structural Similarity Index)**
* **FID (Fréchet Inception Distance)**

---

## 🧠 Motivation

While ResNet-based video generators are efficient, they often suffer from **blurry frames** due to their inherently **discrete modeling** of time. On the other hand, Neural ODEs provide a **continuous-time representation**, making them ideal for modeling smooth temporal transitions, albeit at the cost of training complexity.

> 🔧 **This project investigates the trade-off** between realism, temporal coherence, and training efficiency using a hybrid ODE-ResNet model.

---

## 🏗️ Model Architecture

* **Latent Dynamics**: Modeled using a Neural ODE/ ResNet block that evolves a latent state over continuous/ discrete time.
* **Decoder**: A decoder maps evolved latent states to video frames.
* **Discriminator**: A 3D CNN that distinguishes real from generated video clips.

---

## 📁 Dataset

* **UCF101** (preprocessed into `.pt` tensors of shape `[16, 3, 64, 64]` per clip)

---

## 🚀 Training

* **Epochs**: 10, 100, 200, 300, 2000
* **Batch Size**: 16
* **Optimizer**: Adam (β₁=0.5, β₂=0.999)
* **Loss**: Binary Cross Entropy with Label Smoothing
* **Evaluation Epochs**: 10, 100, 200, 300, 2000

### Logs & Output

* Logs shapes of real and fake videos for consistency.
* Visualizes generated frames vs. real frames.

---

## 📊 Evaluation

* **SSIM**: Measures perceptual similarity between generated and real frames.
* **FID**: Compares statistics of real vs. fake image features.

Results are plotted across evaluation epochs.

---

## 📦 Requirements

```bash
pip install torchdiffeq==0.2.3 scikit-image pytorch-fid
```

---

## 💡 Key Findings

* Neural ODEs improve **temporal continuity** but **slow down training**.
* ResNet decoder handles **spatial detail** but alone produces **blurred frames**.
* The **hybrid approach balances** these strengths, but tuning is critical for convergence.

---

## 📌 Future Work

* Explore **efficient ODE solvers** or **Neural CDEs** for faster training.
* Experiment with **attention-based decoders**.
* Integrate **conditional generation** (e.g., class-conditional GANs).

---

## 👨‍🔬 Author

**Aisha Hamad**
*Data Scientist | ML Researcher*
Reach out for collaborations or research discussions!

---

## 📝 Citation

If you use this code or ideas in your research, please cite:

```bibtex
@misc{hybridode2025,
  title={Hybrid Neural ODE-ResNet Video Generation},
  author={Aisha Hamad},
  year={2025},
  howpublished={GitHub Repository},
  url={https://github.com/Aishahamad01/UCF101}
}
```
