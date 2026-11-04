# 🌿 Leaf Classifier (MLR Exercise 8)

A deep learning leaf classifier fine-tuned in PyTorch using MobileNet, exported to ONNX, and deployed to run entirely in the browser using ONNX Runtime Web.

## 📱 Live Demo (GitHub Pages)
👉 **[Open Live App on your Phone](https://bahriadsay.github.io/mlr-ex08/)**  


---

## 🎯 Overview
This project classifies leaves into four tree species:
- 🍎 **Apple** (*Malus domestica*)
- 🍒 **Cherry** (*Prunus*)
- 🌰 **Chestnut** (*Castanea sativa*)
- 🍁 **Maple** (*Acer*)

The model was fine-tuned on real leaf photos collected during the laboratory session.

---

## 🛠️ Tech Stack & Architecture
- **Framework:** PyTorch (torchvision MobileNet)
- **Export Format:** ONNX (`leaf_model.onnx`, 96×96 RGB input)
- **Inference Engine:** ONNX Runtime Web (`ort.min.js`, WASM/WebGL backend)
- **Deployment:** GitHub Pages (static client-side web application, runs 100% on-device in mobile browser)

---

## 📁 Repository Structure
| File | Description |
| :--- | :--- |
| `index.html` | Interactive web application with live camera and test verification modes |
| `leaf_model.onnx` | Exported PyTorch MobileNet model |
| `model_info.json` | Metadata containing class labels, input size (96×96), mean and std normalization |
| `check_image.jpg` | Verification sample image from the training notebook |
| `check_expected.json` | Baseline prediction probabilities computed by the notebook for `check_image.jpg` |
| `REVIEW.md` | Verification report, notebook probability comparison, and mobile test screenshot |
| `REPORT.md` | Task 4 experimentation report comparing model improvements |
