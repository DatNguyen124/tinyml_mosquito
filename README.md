# Mosquito Classification Using TinyML

This repository contains the source code and resources for the **Mosquito Classification Project** utilizing **TinyML** techniques. The project focuses on classifying mosquito species based on wingbeat sound patterns with lightweight models suitable for deployment on resource-constrained devices such as microcontrollers.

---

## Overview

### Project Objective
- To classify mosquito species into four categories—**Aedes**, **Anopheles**, **Culex**, and **Noise**—using wingbeat sounds, leveraging **1D-CNN models** optimized for TinyML and real-time applications.
- Approach tinyML, lightweight model and edge processing

### Key Features
- **Lightweight 1D-CNN Model:** Designed for edge deployment.
- **Real-Time Inference:** Runs efficiently on devices like the Seeed Studio XIAO nRF52840 Sense.
- **Noise Robustness:** Includes background noise handling for real-world applications.
- **Cost-Effective Deployment:** Suitable for resource-limited environments.

### Pipeline
![Pipeline Overview](Project%20Pipelines/Pipeline1.png "Pipeline 1")
![Pipeline Overview](Project%20Pipelines/Pipeline2.png "Pipeline 2")
### Hardware Usage


### Model


---

## Repository Structure

```
├── arduino code
│   ├── examples
│   │   ├── esp32
│   │   │   ├── esp32_microphone              # Example for ESP32 microphone input
│   │   │   └── esp32_microphone_continuous   # Continuous input example for ESP32 microphone
│   │   ├── nano_ble33_sense
│   │   │   ├── nano_ble33_sense_microphone              # BLE33 Sense microphone input
│   │   │   └── nano_ble33_sense_microphone_continuous   # Continuous BLE33 Sense microphone input
│   │   ├── nano_ble33_sense_rev2
│   │   │   ├── nano_ble33_sense_rev2_microphone         # Updated BLE33 Sense microphone example
│   │   │   └── nano_ble33_sense_rev2_microphone_continuous # Continuous microphone example for BLE33 Sense rev2
│   │   ├── nicla_vision
│   │   │   ├── nicla_vision_microphone             # Microphone example for Nicla Vision
│   │   │   └── nicla_vision_microphone_continuous  # Continuous microphone example for Nicla Vision
│   │   ├── portenta_h7
│   │   │   ├── portenta_h7_microphone             # Portenta H7 microphone example
│   │   │   └── portenta_h7_microphone_continuous  # Continuous Portenta H7 microphone example
│   │   ├── rp2040
│   │   │   ├── rp2040_microphone              # RP2040 microphone input
│   │   │   └── rp2040_microphone_continuous   # Continuous microphone input for RP2040
│   │   ├── sony_spresense
│   │   │   ├── sony_spresense_microphone             # Microphone example for Sony Spresense
│   │   │   └── sony_spresense_microphone_continuous  # Continuous microphone example for Sony Spresense
│   │   └── static_buffer
│   │       └── static_buffer                  # Static buffer example for audio processing
│   └── src
│       ├── edge-impulse-sdk
│       │   ├── classifier                     # Core model inferencing logic
│       │   ├── dsp                            # DSP functions for audio preprocessing
│       │   ├── tensorflow                     # TensorFlow Lite Micro library
│       │   └── third_party                    # Third-party libraries (Flatbuffers, Gemmlowp, etc.)
│       ├── model-parameters                   # Model-specific parameters
│       └── tflite-model                       # Exported TensorFlow Lite model
├── datasets
│   ├── Abuzz
│   │   ├── Ae. aegypti                        # Wingbeat data for Ae. aegypti
│   │   ├── Ae. albopictus                     # Wingbeat data for Ae. albopictus
│   │   ├── An. arabiensis                     # Wingbeat data for An. arabiensis
│   │   ├── An. gambiae                        # Wingbeat data for An. gambiae
│   │   ├── C. pipiens                         # Wingbeat data for C. pipiens
│   │   └── C. quinquefasciatus                # Wingbeat data for C. quinquefasciatus
│   └── Abuzz_Preprocessed
│       ├── aedes                              # Preprocessed spectrograms for Aedes class
│       ├── anopheles                          # Preprocessed spectrograms for Anopheles class
│       ├── culex                              # Preprocessed spectrograms for Culex class
│       └── noise                              # Preprocessed spectrograms for Noise class
├── mic_test                                   # Scripts for testing microphone performance
├── notebooks
│   ├── data_preprocessing.ipynb               # Preprocessing pipeline in Jupyter
│   ├── model_training.ipynb                   # Model training and evaluation in Jupyter
├── Project Pipelines                          # Documentation for project workflows
```

---

## Optimized File Usage in Arduino

The `arduino code` folder focuses on sound-related examples and libraries:

- **Microphone Examples:**
  - Examples tailored for devices such as ESP32, BLE33 Sense, Nicla Vision, Portenta H7, and RP2040.
  - Continuous microphone examples for real-time inferencing.

- **Static Buffer Example:**
  - Demonstrates audio processing using static buffers, ideal for resource-constrained devices.

- **Edge-Impulse-SDK:**
  - Contains core libraries for running TinyML models on microcontrollers.
  - Includes DSP functions for audio feature extraction and TensorFlow Lite Micro libraries for inferencing.

---

## Usage Guide

### Creating the `mos_inferencing` Library with Edge Impulse
1. **Data Upload:**
   - Upload the preprocessed spectrogram data to Edge Impulse Studio.
   - Follow the pipeline in Edge Impulse for feature generation and model training.

2. **Model Training:**
   - Train the 1D-CNN model in Edge Impulse using the spectrogram dataset.
   - Validate the model to ensure it achieves the desired accuracy (target: 93.32%).

3. **Model Export:**
   - Export the trained model as an Arduino library.
   - In Edge Impulse, navigate to the *Deployment* section and select *Arduino Library*.
   - Download and extract the library files (e.g., `mos_inferencing.h` and `mos_inferencing.cpp`).

4. **Integrate with Arduino IDE:**
   - Copy the exported library files to the Arduino `libraries` folder.
   - Open `mosquito_classification.ino` and include the library.

### Using the Library in Arduino
1. **Hardware Setup:**
   - Use the **Seeed Studio XIAO nRF52840 Sense** for deployment.
   - Configure the onboard microphone for audio capture.

2. **Uploading the Code:**
   - Open `mosquito_classification.ino` in Arduino IDE.
   - Ensure the correct board and port are selected.
   - Upload the code to the microcontroller.

3. **Real-Time Testing:**
   - Test with live audio input or sample mosquito wingbeat audio files.
   - Observe classification results via serial monitor or connected indicators (e.g., LEDs).

---

## Results
- **Classification Accuracy:** 93.32%.
- **Robust Noise Handling:** Effectively differentiates noise from mosquito species.
- **Efficient Edge Deployment:** Runs on low-power devices.

---

## Future Improvements
- Enhance noise cancellation for diverse environments.
- Expand the dataset to include additional mosquito species.
- Integrate real-time data with public health systems.

---

## Contributing
Contributions are welcome! Feel free to open an issue or submit a pull request to improve the project.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact
- **Authors:** Dinh Thai Duy & Nguyen Man Dat
- **Email:** 10421014@student.vgu.edu.vn - 10421008@student.vgu.edu.vn
