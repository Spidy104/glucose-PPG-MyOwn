# Glucose-PPG Dataset & CNN Modeling

**Contact:** iamdibs23@gmail.com

This project provides an open dataset of synchronized blood glucose and PPG (photoplethysmography) readings, aiming to explore the relationship between them using convolutional neural networks (CNNs). The ultimate goal is to enable continuous, noninvasive blood glucose monitoring using PPG signals.

---

## Dataset Overview

- **Blood Glucose Readings:**  
  Collected using a commercial minimally invasive continuous glucose monitor (CGM). The sensor uses a tiny electrode inserted ~5mm under the skin, providing real-time glucose data every 2 minutes for up to 14 days.

  <img src="imgs/sensor1.png" width="30%"> <img src="imgs/sensor2.jpg" width="30%">
  <img src="imgs/sensor3.jpg" width="30%"> <img src="imgs/d1.jpg" width="30%">

- **PPG Readings:**  
  Acquired from a pulse oximeter development board. PPG is widely used in consumer devices (watches, fitness bands) for heart rate and blood oxygen measurement. It is completely noninvasive, fast (results in seconds), and affordable (typical devices cost $20–30 USD).

  <img src="imgs/HOLYCHIP0541+BT.jpg" width="30%"> <img src="imgs/app.jpg" width="30%">

---

## Motivation

Traditional blood glucose monitoring often requires finger-pricking, which is painful and inconvenient for frequent testing. While CGMs are more convenient, they are expensive and not accessible to everyone. This project investigates whether PPG—a fast, cheap, and noninvasive method—can be used to estimate blood glucose levels.

---

## Data Format

- Each data file (~30KB) contains multiple data packets.
- **Packet structure:**  
  - Starts with `11551155`
  - Followed by 16 numbers:  
    - Even indices: IR light intensity  
    - Odd indices: LED light intensity  
  - Each packet represents a sample starting at the trough of the heart rate waveform, with light intensity sampled every 2ms.
- **File naming convention:**  
  `HHH_SSS_XXX_GGG`  
  - `HHH`: Heart rate (3 digits)  
  - `SSS`: SaO2 (3 digits)  
  - `XXX`: Finger (0=not recorded, 1=thumb ... 5=pinky)  
  - `GGG`: Glucose (10 × mmol/L)

  <img src="imgs/datalist.png" width="30%">
  <img src="imgs/datapacket.png" width="30%">

---

## Usage

- See `glucose.ipynb` for data loading and CNN modeling examples.
- Several CNN architectures have been tested. While validation MAE is below 3, real-world generalization remains challenging. Contributions and suggestions for improvement are welcome!

---

## ⚠️ Build Failing: TensorFlow Not Available

**Note:**  
This project requires TensorFlow (tested with TensorFlow 2.x and Keras 2.3).  
TensorFlow is **not available for Python versions above 3.11** as of May 2025.  
If you see errors like `ModuleNotFoundError: No module named 'tensorflow'` or `Could not find a version that satisfies the requirement tensorflow`, please:

- Use Python 3.10 or 3.11 (64-bit recommended)
- Upgrade pip:  
  `python -m pip install --upgrade pip`
- Then install TensorFlow:  
  `pip install tensorflow`

If you are using Python 3.12 or newer, please downgrade your Python version to run this project.

---

## Download

- **Dataset & Source Code:**  
  [https://github.com/Spidy104/glucose-PPG-MyOwn](https://github.com/Spidy104/glucose-PPG-MyOwn)

---

**Questions or suggestions?**  
Feel free to open an issue or contact: iamdibs23@gmail.com



