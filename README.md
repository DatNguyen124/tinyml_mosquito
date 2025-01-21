# Mosquito Classification Using TinyML

This repository contains the source code and resources for the **Mosquito Classification Project** using **TinyML** techniques. The project focuses on classifying mosquito species based on wingbeat sound patterns with lightweight models suitable for deployment on resource-constrained devices such as microcontrollers.

---

## Overview

### Project Objective
To classify mosquito species into four classes—**Aedes**, **Anopheles**, **Culex**, and **Noise**—using wingbeat sounds, leveraging **1D-CNN models** optimized for TinyML and real-time applications.

### Key Features
- **Lightweight 1D-CNN Model:** Designed for edge deployment.
- **Real-Time Inference:** Runs efficiently on devices like the Seeed Studio XIAO nRF52840 Sense.
- **Noise Robustness:** Includes background noise handling for real-world applications.
- **Cost-Effective Deployment:** Suitable for resource-limited environments.

---

## Repository Structure

```
├── python-files
│   ├── data_preprocessing.py   # Scripts for audio preprocessing and spectrogram generation
│   ├── model_training.py       # Training and optimization of the 1D-CNN model
│   ├── model_conversion.py     # Convert trained model to TensorFlow Lite format
│   ├── utils.py                # Helper functions for data processing
│
├── arduino-files
│   ├── mosquito_classification.ino  # Arduino code for deploying and testing the model
│   ├── model.h                     # Converted model for Arduino (Edge Impulse export)
│
├── datasets
│   ├── WINGBEATS                 # Example dataset folder
│   ├── ABUZZ                     # Example dataset folder
│
├── notebooks
│   ├── data_visualization.ipynb  # Jupyter notebook for exploring and visualizing data
│   ├── training_results.ipynb    # Jupyter notebook for analyzing model performance
│
├── README.md                     # Documentation (this file)
├── LICENSE                       # Project license
├── requirements.txt              # Python dependencies
```

---

## Getting Started

### Prerequisites
1. Python 3.9 or later.
2. Required libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Arduino IDE with necessary board libraries (e.g., Seeed Studio XIAO nRF52840 Sense).

### Setup Instructions

#### Clone Repository
```bash
git clone https://github.com/<your-username>/mosquito-classification.git
cd mosquito-classification
```

#### Data Preparation
1. Place raw mosquito wingbeat audio files in the `datasets` folder.
2. Run `data_preprocessing.py` to preprocess and generate spectrograms:
   ```bash
   python python-files/data_preprocessing.py
   ```

#### Model Training
Train the 1D-CNN model:
```bash
python python-files/model_training.py
```

#### Model Conversion
Convert the trained model to TensorFlow Lite format for deployment:
```bash
python python-files/model_conversion.py
```

#### Deployment
1. Export the converted model as a `.h` file.
2. Open `arduino-files/mosquito_classification.ino` in Arduino IDE.
3. Upload the code and model to your microcontroller.

---

## Results
- **Classification Accuracy:** 93.32%
- **Precision & Recall:** High performance across all mosquito species.
- **Inference Time:** Optimized for real-time classification on edge devices.

---

## Future Improvements
- Enhance noise reduction for diverse environments.
- Expand dataset to include additional mosquito species.
- Integrate with public health surveillance systems.

---

## Contributing
Contributions are welcome! Please open an issue or submit a pull request to suggest improvements or report bugs.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Acknowledgments
- **Supervisor:** Dr. Vo Bich Hien
- **Institutions:** Vietnamese-German University & Frankfurt University of Applied Sciences

---

## Contact
- **Author:** Dinh Thai Duy & Nguyen Man Dat
- **Email:** [your-email@example.com]
