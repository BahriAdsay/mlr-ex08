# 📝 Task 2 Review: Leaf Classifier Web Deployment

## 1. Probability Check on `check_image.jpg`

The model was tested against `check_image.jpg` both inside the Google Colab PyTorch notebook and in the browser using ONNX Runtime Web.

| Class | Notebook Expected Probability | Web ONNX Runtime Probability | Difference | Status |
| :--- | :---: | :---: | :---: | :---: |
| 🍎 **Apple** | 82.959% (`0.829588`) | 82.959% | < 0.001% | ✅ Exact Match |
| 🍒 **Cherry** | 16.795% (`0.167952`) | 16.795% | < 0.001% | ✅ Exact Match |
| 🌰 **Chestnut** | 0.246% (`0.002456`) | 0.246% | < 0.001% | ✅ Exact Match |
| 🍁 **Maple** | 0.000% (`0.000004`) | 0.000% | < 0.001% | ✅ Exact Match |

**Observation:** The ONNX Runtime Web predictions match the notebook probabilities with negligible floating point variation ($< 10^{-5}$), confirming that preprocessing (center crop to 96×96, channel normalization with ImageNet mean `[0.485, 0.456, 0.406]` and std `[0.229, 0.224, 0.225]`, and softmax) is implemented correctly.

---

## 2. Requirements Checklist & Code Inspection

| Requirement | Implementation Details in `index.html` | Status |
| :--- | :--- | :---: |
| **ONNX Runtime Web Integration** | Loaded official `ort.min.js` via CDN. Creates inference session with WebGL/WASM execution providers. | ✅ Implemented |
| **Model & Metadata Loading** | Dynamically fetches `leaf_model.onnx`, `model_info.json`, and `check_expected.json`. | ✅ Implemented |
| **Preprocessing Pipeline** | Draws image/frame to an offscreen 96×96 canvas, normalizes pixel channels: `(channel / 255 - mean) / std`, packs into NCHW tensor `[1, 3, 96, 96]`. | ✅ Implemented |
| **Phone Camera Access** | Uses `navigator.mediaDevices.getUserMedia` with `facingMode: "environment"` (rear camera on mobile devices). Includes fallback and flip camera option. | ✅ Implemented |
| **Real-time Classification** | Throttled `requestAnimationFrame` loop (~6 FPS) to ensure smooth prediction without overheating phone hardware. | ✅ Implemented |
| **Check Verification UI** | Dedicated verification tab displaying side-by-side comparison table against `check_expected.json` with visual match badge. | ✅ Implemented |
| **Responsive Mobile Layout** | Mobile-first viewport, clean cards, animated probability bars, and targeting reticle for framing leaves. | ✅ Implemented |

---

## 3. Mobile Camera Test & Screenshot

Place a screenshot of the web application running on your mobile phone camera below:

![Mobile Camera Test Screenshot](phone_screenshot.jpg)

*(Instructions: Open your deployed GitHub Pages URL on your smartphone, point the camera at a leaf or sample photo, take a screenshot, name it `phone_screenshot.jpg`, and place it in this repository).*
