# Mosquito Classification Using TinyML

This repository contains the source code and resources for the **Mosquito Classification Project** utilizing **TinyML** techniques. The project focuses on classifying mosquito species based on wingbeat sound patterns with lightweight models suitable for deployment on resource-constrained devices such as microcontrollers.

---

## Overview
Module: PROJECT
Supervisor: Dr. Vo Bich Hien
### Project Objective
- To classify mosquito species into four categories—**Aedes**, **Anopheles**, **Culex**, and **Noise**—using wingbeat sounds, leveraging **1D-CNN models** optimized for TinyML and real-time applications.
- Approach tinyML, lightweight model and edge processing

### Key Features
- **Lightweight 1D-CNN Model:** Designed for edge deployment.
- **Real-Time Inference:** Runs efficiently on devices like the Seeed Studio XIAO nRF52840 Sense.
- **Noise Robustness:** Includes background noise handling for real-world applications.
- **Cost-Effective Deployment:** Suitable for resource-limited environments.

### Pipeline
<figure>
    <img src="Project%20Pipelines/Pipeline1.png" alt="Pipeline 1 Overview" title="Pipeline 1" style="width: 60%;">
    <figcaption></figcaption>
</figure>

**Pipeline 1** employs TinyML for low-power and cost-effective mosquito species classification. This pipeline is specifically designed for deployment in remote or resource-constrained environments. <br>

**Advantages:**
- **Energy Efficiency:** Operates on minimal power, enabling extended use on battery-powered devices.
- **Cost Savings:** Avoids reliance on cloud computing, reducing deployment and operational expenses.
- **Compact Design:** Utilizes microcontrollers such as the Arduino Nano 33 BLE Sense, ensuring portability and practicality in the field. <br>

**Limitations:**
- **Model Constraints:** Requires lightweight models, which can limit classification accuracy and complexity.
- **Optimization Challenges:** Demands advanced techniques like model pruning and quantization to meet hardware constraints while maintaining real-time responsiveness. <br>

This pipeline highlights the balance between performance and resource limitations inherent to embedded systems. The next sections will explore the hardware and software decisions that enable the success of this pipeline. <br>

<figure>
    <img src="Project%20Pipelines/Pipeline2.png" alt="Pipeline 2 Overview" title="Pipeline 2" style="width: 60%;">
    <figcaption></figcaption>
</figure>

Pipeline 2 leverages Edge Impulse for live classification directly at the edge, offering several key benefits. <br>
**Advantages:**
- **Real-Time Processing:** Ensures immediate classification results without reliance on cloud infrastructure.
- **Ease of Deployment:** Utilizes a user-friendly platform with pre-built tools, accelerating development and deployment cycles.
- **Reduced Latency:** Processes data locally on the device, minimizing delays compared to cloud-dependent workflows. <br>

**Limitations:**
- **Device Compatibility:** Performance heavily depends on the capabilities of the deployed hardware, requiring careful hardware selection.
- **Resource Constraints:** Optimization is necessary to balance accuracy and efficiency on low-power devices.
- **Scalability Challenges:** Tailored adjustments are needed for deployment across diverse hardware setups.

This pipeline demonstrates the potential of edge-based systems for scalable and efficient mosquito classification. The following sections will delve deeper into the optimizations and decisions underlying this approach.

### Hardware Usage
Initially, the Arduino Nano 33 BLE Sense was considered ideal for this project due to its powerful hardware and compatibility with TinyML frameworks. However, the high cost of this device in Vietnam made it less practical for deployment. As an alternative, we chose the Seeed Studio XIAO nRF52840 Sense, which offers similar hardware specifications at a more affordable price point. This decision ensures cost-effectiveness while maintaining the computational capabilities required for real-time mosquito classification.

#### Comparison of Arduino Nano 33 BLE Sense and Seeed Studio XIAO nRF52840 Sense:

| Feature                          | Arduino Nano 33 BLE Sense                        | Seeed Studio XIAO nRF52840 Sense              |
|----------------------------------|--------------------------------------------------|-----------------------------------------------|
| Processing Unit                  | Nordic Semiconductor nRF52840 SoC, 32-bit ARM Cortex-M4 CPU (64 MHz) | Nordic Semiconductor nRF52840 SoC, 32-bit ARM Cortex-M4 CPU (64 MHz) |
| Memory                           | 256 KB RAM, 1 MB Flash                           | 256 KB RAM, 1 MB Flash                       |
| Connectivity                     | Bluetooth 5.0 (BLE), NFC                         | Bluetooth 5.0 (BLE), NFC, USB-C              |
| Sensors                          | Environmental (temperature, humidity, pressure), motion (accelerometer, gyroscope), microphone | Environmental (temperature, humidity, pressure), motion (accelerometer, gyroscope), microphone |
| Power                            | Low-power design                                  | Low-power design, battery-friendly            |
| Peripherals                      | UART, I2C, SPI, PWM, ADC, GPIO                   | UART, I2C, SPI, PWM, ADC, GPIO               |
| Development Tools                | Arduino IDE, CircuitPython, Edge Impulse, TinyML | Arduino IDE, CircuitPython, Edge Impulse, TinyML |
| Form Factor                      | 45 x 18 mm                                       | 21 x 17.5 mm                                 |
| Price                            | ∼ 1,400,000 VND (approx.)                        | ∼ 500,000 VND (approx.)                      |

**Table 4.1:** Comparison of Arduino Nano 33 BLE Sense and Seeed Studio XIAO nRF52840 Sense

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
   - Follow the pipeline in Edge Impulse (as shown in the image below) for feature generation and model training.
![image](https://github.com/user-attachments/assets/22502a72-0865-407d-a4df-37f468b825e6)
![image](https://github.com/user-attachments/assets/19961659-4ce5-4a54-8ceb-23520c96f027)


2. **Model Training:**
   - Train the 1D-CNN model in Edge Impulse using the spectrogram dataset. Model detailed is attached in this image below.
   - Validate the model to ensure it achieves the desired accuracy (target: 93.32%).
![image](https://github.com/user-attachments/assets/9a71a03e-1707-4b41-a529-d5b75d03d978)

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
   - Observe classification results via a serial monitor or connected indicators (e.g., LEDs).

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
- Working with Pipeline 2

---

## Contributing
Contributions are welcome! Feel free to open an issue or submit a pull request to improve the project.

---


## Contact
- **Authors:** Dinh Thai Duy & Nguyen Man Dat
- **Email:** 10421014@student.vgu.edu.vn - 10421008@student.vgu.edu.vn
