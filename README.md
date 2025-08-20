# Wheat Detection with YOLO11n 🌾

![Wheat Detection](https://img.shields.io/badge/YOLO-v11n-blue) ![Python](https://img.shields.io/badge/Python-3.8%2B-green) ![Ultralytics](https://img.shields.io/badge/Ultralytics-8.0.0-orange)

A project for detecting wheat heads in images using the YOLO11n model from Ultralytics. This repository includes dataset setup, model training, and inference with visualization for the GlobalWheat2020 dataset. 🚀

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Dataset](#dataset)
- [Usage](#usage)
- [Training](#training)
- [Inference](#inference)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## 🌟 Overview
This project leverages the power of the YOLO11n model to detect wheat heads in agricultural images. It uses the GlobalWheat2020 dataset, automates dataset organization, trains a model, and performs inference with visualized bounding boxes. Perfect for computer vision enthusiasts and agricultural tech researchers! 📸

## ✨ Features
- 🛠️ Installs Ultralytics for YOLO model support
- 📂 Downloads and organizes the GlobalWheat2020 dataset
- ⚙️ Trains YOLO11n for wheat head detection
- 🖼️ Visualizes detection results with bounding boxes
- 🔄 Supports further training and inference

## 🛠️ Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/shahin-ro/wheat-detection.git
   cd wheat-detection
   ```
2. Install dependencies:
   ```bash
   pip install ultralytics
   ```

> **Note**: This project is designed to run in a Google Colab environment for easy access to GPU resources. Adjust paths if running locally.

## 📊 Dataset
The project uses the [GlobalWheat2020 dataset](https://zenodo.org/record/4298502). The script:
- Downloads images and annotations
- Organizes them into `images`, `annotations`, and `labels` directories
- Creates a `GlobalWheat2020_subset.yaml` file for training and validation subsets

## 🚀 Usage
1. **Setup**: Run the dataset setup code to download and organize the GlobalWheat2020 dataset.
2. **Train**: Train the YOLO11n model using the provided YAML configuration.
3. **Infer**: Upload an image and detect wheat heads with visualized results.

## 🏋️‍♂️ Training
Train the model with the following command in the script:
```python
model = YOLO("yolo11n.pt")
model.train(data="GlobalWheat2020_subset.yaml", epochs=5, imgsz=640)
```
- Adjust `epochs` or `imgsz` for better results.
- Trained weights are saved in `/content/runs/detect/train/weights/best.pt`.

## 🔍 Inference
Perform inference on a new image:
```python
model = YOLO("/content/runs/detect/train/weights/best.pt")
results = model("path/to/your/image.jpg")
for result in results:
    img = result.plot()
    plt.imshow(img)
    plt.axis('off')
    plt.show()
```
Upload an image in Colab to see bounding boxes around detected wheat heads.

## 📈 Results
The model outputs bounding boxes around wheat heads in the input images. Results are visualized using Matplotlib, showing detected wheat heads with confidence scores.

## 🤝 Contributing
Contributions are welcome! 🌟
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit changes (`git commit -m 'Add YourFeature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

## 📜 License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

🌾 Happy wheat detection! If you find this project useful, give it a ⭐ on GitHub!
