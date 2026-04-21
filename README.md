# ♻️ Waste Classification System

> AI-powered waste classification using deep learning and Flask. Upload an image, get an instant prediction.

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x-000000?logo=flask)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?logo=tensorflow&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-22c55e)

---

## Overview

The Waste Classification System is a deep learning web application that identifies waste types from uploaded images. It supports six categories — **cardboard, glass, metal, paper, plastic, and trash** — and displays confidence percentages for each prediction, making it a practical tool for smart recycling and waste management.

---

## Features

- **Image Upload Interface** — Drag-and-drop or browse to upload waste images
- **Real-time Classification** — Sub-second inference powered by a trained CNN
- **Six Waste Categories** — Cardboard · Glass · Metal · Paper · Plastic · Trash
- **Confidence Visualization** — Percentage bars for all category scores
- **REST API** — JSON endpoint for programmatic access
- **Mobile Responsive** — Fully adaptive layout across all screen sizes

---

## Getting Started

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Bittu-kumar143/wastesegregation_ai-ml_project.git
cd wastesegregation_ai-ml_project

# 2. Create and activate a virtual environment (recommended)
python -m venv venv

# Linux/macOS
source venv/bin/activate

# Windows
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the application
python app.py
```

The server starts at **http://localhost:5000**

---

## Project Structure

```
waste-classifier/
│
├── app.py                  # Flask application entry point
├── config.py               # Configuration settings
├── requirements.txt        # Python dependencies
│
├── model/
│   ├── classifier.py       # Model architecture and inference logic
│   ├── weights.h5          # Pre-trained model weights
│   └── preprocess.py       # Image preprocessing utilities
│
├── templates/
│   └── index.html          # Frontend UI
│
├── static/
│   ├── css/                # Stylesheets
│   └── js/                 # JavaScript
│
├── dataset/
│   ├── train/              # Training images (by category)
│   └── test/               # Test images
│
└── uploads/                # Temporary storage for uploaded images
```

---

## API Reference

### `POST /predict`

Classify a waste image.

**Request**
```bash
curl -X POST http://localhost:5000/predict \
  -F "file=@your_image.jpg"
```

**Response**
```json
{
  "prediction": "plastic",
  "confidence": 0.94,
  "all_scores": {
    "cardboard": 0.01,
    "glass": 0.02,
    "metal": 0.01,
    "paper": 0.01,
    "plastic": 0.94,
    "trash": 0.01
  }
}
```

---

## Waste Categories

| Category    | Description                              |
|-------------|------------------------------------------|
| Cardboard   | Boxes, cartons, corrugated paper         |
| Glass       | Bottles, jars, broken glass              |
| Metal       | Cans, foil, metal containers             |
| Paper       | Newspapers, magazines, office paper      |
| Plastic     | Bottles, bags, packaging                 |
| Trash       | General non-recyclable waste             |

---

## Model Details

The classifier is a Convolutional Neural Network (CNN) trained on a labeled dataset of waste images. Images are resized and normalized before inference. The model outputs a softmax distribution across the six waste categories.

- **Input size:** 224 × 224 px
- **Architecture:** Custom CNN / Transfer Learning (ResNet50)
- **Output:** 6-class softmax probability distribution

---

## Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "Add my feature"`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a Pull Request

Please ensure your changes pass existing tests before submitting.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Acknowledgements

- Dataset inspired by the [TrashNet](https://github.com/garythung/trashnet) project
- Built with [Flask](https://flask.palletsprojects.com/) and [TensorFlow](https://www.tensorflow.org/)
