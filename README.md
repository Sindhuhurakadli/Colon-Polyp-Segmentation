# Colon-Polyp-Segmentation
PVT-MiniUNet: A Lightweight Transformer for Colon Polyp Segmentation in Resource Constrained Clinical Settings


# 🩺 PVT-MiniUNet: Lightweight Transformer for Colon Polyp Segmentation

## 📌 Overview

Colorectal cancer (CRC) is one of the leading causes of cancer-related deaths worldwide. Detecting **colon polyps** early during colonoscopy is crucial for prevention, but automatic segmentation is difficult due to:

* High variability in polyp size, shape, and texture
* Low contrast with surrounding tissue
* Motion blur, lighting issues, and specular highlights


## 🚀 Key Contributions

* **Pyramid Vision Transformer v2 (PVTv2-B2) Encoder**
  Captures **multi-scale global and local features** efficiently.

* **Mini-UNet Decoder (replacing SAM)**
  Recovers **fine spatial details** with lower complexity.
  → Improves polyp boundary segmentation.

* **Camouflage Identification Module (CIM)**
  Highlights **subtle boundaries** where polyps blend with surrounding tissue.

* **Cascaded Fusion Module (CFM)**
  Merges multi-scale features for better context understanding.



## 🔬 Methodology

1. Input colonoscopy image passed through **PVTv2 Encoder** → extracts hierarchical features.
2. **CFM** integrates deep semantic features across scales.
3. **CIM** enhances boundary visibility and fine details.
4. **Mini-UNet Decoder** combines CFM + CIM outputs → reconstructs accurate segmentation mask.
5. Output: **Binary polyp mask** aligned with input image.


## 📊 Results (Kvasir-SEG Dataset)

| Model                     | IoU        | Dice Score |
| ------------------------- | ---------- | ---------- |
| DUCK-Net                  | 0.9502     | 0.9051     |
| EffiSegNet                | 0.9488     | 0.9065     |
| UPolySeg                  | 0.9686     | 0.8791     |
| Multi-Layer Dense Decoder | 0.9190     | 0.8690     |
| **Polyp-PVT (Baseline)**  | 0.9170     | 0.8640     |
| **PVT-MiniUNet (Ours)**   | **0.9158** | **0.9550** |

✅ **Improves Dice score by +9.1%** and IoU by +6.9% over baseline Polyp-PVT.
✅ Uses **25.14M params** & **10.15 GMACs**, making it suitable for **real-time, low-resource deployment**.


## 🎯 Conclusion

PVT-MiniUNet achieves a strong **balance between efficiency and accuracy**:

* Outperforms baseline Polyp-PVT in segmentation accuracy.
* Lightweight enough for **real-time clinical use on edge devices**.
* Excels in handling **low-contrast, camouflaged, and variable polyps**.

