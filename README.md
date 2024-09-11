# TinyML Face Detection using Arduino UNO and OV7675 Camera

This project demonstrates face detection on an Arduino UNO using the TinyML framework. The OV7675 camera is used to capture images, and a pre-trained MobileNet model along with a keyword spotter model is deployed on the Arduino to detect faces in real-time.

## Table of Contents

- [Overview](#overview)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Setup and Installation](#setup-and-installation)
- [Model Training](#model-training)
- [Deploying the Model](#deploying-the-model)
- [Running the Project](#running-the-project)
- [Troubleshooting](#troubleshooting)
- [Future Work](#future-work)
- [License](#license)

## Overview

This project implements a face detection system on low-power microcontrollers like the Arduino UNO. The system uses the OV7675 camera to capture images, and a pre-trained MobileNet model paired with a keyword spotter model is deployed using TensorFlow Micro to detect faces.

![WhatsApp Image 2023-07-04 at 15 00 33_6e741b96](https://github.com/user-attachments/assets/bc9027e9-50cf-48a3-bca6-ceb859d8eafa "Image captured using OV7675 Camera")


## Hardware Requirements

- **Arduino UNO**
- **OV7675 Camera Module**
- **Breadboard and Jumper Wires**
- **USB Cable for Arduino**
- **Computer with Arduino IDE**

## Software Requirements

- **Arduino IDE** (latest version)
- **TinyML library** (installed via Arduino Library Manager)
- **TensorFlow Lite for Microcontrollers** (for deploying the model)
- **Edge Impulse CLI** (for model training and deployment)
- **Python** (for preprocessing and training the model)

## Setup and Installation

1. **Arduino IDE Setup**: 
    - Download and install the [Arduino IDE](https://www.arduino.cc/en/software).
    - Install the required libraries using the Library Manager (`TinyML`, `OV7675`, etc.).

2. **Camera Setup**: 
    - Connect the OV7675 camera module to the Arduino UNO according to the following pin configuration:
      - Camera VCC to Arduino 5V
      - Camera GND to Arduino GND
      - Camera SDA to Arduino A4
      - Camera SCL to Arduino A5

3. **Install Edge Impulse CLI**:
    - Install [Edge Impulse CLI](https://docs.edgeimpulse.com/docs/cli-installation) for training and deploying the model.

## Model Training

1. **Data Collection**:
    - Use the Edge Impulse platform to collect face images. Connect your Arduino UNO and OV7675 camera to capture images directly into the platform.

2. **Preprocessing**:
    - Preprocess the images to resize and normalize them for training. This can be done directly in Edge Impulse or using a Python script.

3. **Training**:
    - We used a pretrained MobileNet model for feature extraction and a keyword spotter model for face detection from TensorFlow Lite.
    - Ensure the models are small enough to fit within the memory constraints of the Arduino UNO (This involves knowledge distillation, quantization etc.)

4. **Exporting the Model**:
    - Export the models in the TensorFlow Lite format compatible with TensorFlow Micro.

## Deploying the Model

1. **Compile and Upload**:
    - Compile the exported models with the Arduino IDE and upload them to your Arduino UNO.
    - Ensure that the TensorFlow Micro models are integrated into your Arduino sketch.


## Running the Project

1. **Power the Arduino UNO**:
    - Connect the Arduino to your computer or a power source.
  
2. **Start the Face Detection**:
    - The system will start capturing images and performing face detection using the MobileNet and keyword spotter models.
    - Say out "Hello" to activate the camera and wait for 5 seconds for inference.
    - You can view the results via the Serial Monitor in the Arduino IDE.

## Troubleshooting

- **Camera Not Detected**: Ensure the connections are correct and the camera is powered.
- **Model Not Loading**: Check memory usage and optimize the models if necessary.
- **No Face Detected**: Adjust the camera position and lighting conditions for better image capture.

## Future Work

- **Improve Accuracy**: Explore more complex models or additional preprocessing steps to improve detection accuracy.
- **Bias Mitigation**: Currently there is a bias towards complexion and timeslot when the image was taken.
- **Real-time Detection**: Optimize the code further for real-time face detection.
- **Improved camera**: Current camera has limitations in terms of FOV and quality of image, we can improve  on camera to enable much better detection.
- **Image Recognition**: We can create a cascading architecture, that will allow us to send the image to a cloud server where it can be processed for image recognition, which is infeasible on chip.


