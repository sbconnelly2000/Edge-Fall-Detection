# TinyFall-Edge-Detection: Real-Time Fall Detection on Edge Hardware

![Project Status](https://img.shields.io/badge/Status-Embedded%20Prototype-green) 
![Platform](https://img.shields.io/badge/Platform-TinyML%20/%20TFLite%20Micro-blue) 
![Model Size](https://img.shields.io/badge/Model%20Size-50kB-orange)
![Inference Speed](https://img.shields.io/badge/Latency-0.04ms-red)

**TinyFall** is an ultra-lightweight 1D Convolutional Neural Network (CNN) designed for geriatric fall detection using Inertial Measurement Unit (IMU) data. Optimized specifically for constrained embedded systems, this model achieves **96.9% accuracy** while fitting entirely within **50kB of memory** and enabling real-time classification with an inference time of just **0.04 milliseconds**.

## 🎯 The Engineering Challenge
The primary goal was to implement a highly accurate fall detection system while adhering to the severe computational constraints of low-power microcontrollers. This necessitated deep architectural optimization and aggressive post-training quantization to maintain high performance with minimal footprint.

## 🖼️ Project Visual Hook

[Embed a GIF/Video/Image here showing the system in action. For example: A screen recording of the raw sensor data stream, the model outputting "Fall" or "Not Fall" in real-time, or a photo of the final hardware setup.]

## 🛠️ Technical Implementation & Optimization

This project demonstrates a full end-to-end TinyML pipeline: from data preprocessing to model deployment on the edge.

### 1. Model Architecture (1D CNN)
* **Input Data:** 3-axis Accelerometer and Gyroscope data sampled at **[INSERT SAMPLING RATE, e.g., 50Hz]**.
* **Design Rationale:** A shallow 1D CNN was chosen for its ability to capture temporal patterns in sensor data efficiently.
* **Key Optimization:** Increased the kernel size in the initial layers (to **[INSERT KERNEL SIZE, e.g., 5 or 7]**) to capture longer time dependencies in the sliding window. Dropout layers were used extensively to combat overfitting and reduce model complexity.

### 2. Edge Deployment & Quantization
* **Target Hardware:** **[INSERT SPECIFIC MICROCONTROLLER, e.g., Arduino Nano 33 BLE Sense / ESP32]**.
* **Quantization:** The trained model was converted to **TFLite format** and aggressively optimized using **[SPECIFY: Post-Training Integer Quantization / Float16]**. This reduced the size by **[ESTIMATE REDUCTION %]** with a minimal $\sim 0.1\%$ drop in accuracy.
* **Inference Loop:** Implements a memory-efficient **sliding window algorithm** to process incoming sensor data continuously, ensuring minimal latency and responsiveness.

## 📊 Performance Metrics

| Metric | Value | Detail |
| :--- | :--- | :--- |
| **Accuracy (Pre-Quantization)** | 97.0% | Based on validation set. |
| **Accuracy (Quantized)** | **96.9%** | **Final deployed performance.** |
| **Model Footprint** | **50 kB** | Size of the `.tflite` file. |
| **Inference Latency** | **0.04 ms** | Time required for one prediction cycle. |
| **Deployment Platform** | **[INSERT HARDWARE NAME]** | Confirms true embedded functionality. |

## 📁 Repository Structure
