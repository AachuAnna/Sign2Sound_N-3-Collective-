# SIGN2SOUND – Sign Language to Speech System

SIGN2SOUND is a real-time sign language to speech system designed to help bridge the communication gap between deaf or hard-of-hearing individuals and people who do not understand sign language.

The system recognizes gestures, classifies them using machine learning, and converts the recognized gesture into audible speech.

---

## Problem Statement

Deaf and hard-of-hearing individuals often face difficulties communicating with the general public. Existing solutions may require human interpreters, cameras, or internet connectivity, which limits accessibility, privacy, and portability.

---

## Solution Overview

SIGN2SOUND captures gesture-related data, processes it through a machine learning pipeline, performs real-time classification, and converts the predicted gesture into speech using text-to-speech technology.  
The system is designed to work offline and can be deployed on edge devices.

---

## Key Features

- Real-time gesture recognition  
- Offline inference support  
- Text-to-speech output  
- Edge device compatibility  
- Privacy-preserving (no camera-based processing)  
- Modular ML pipeline  

---

## System Architecture

1. Gesture data acquisition  
2. Data preprocessing and augmentation  
3. Feature extraction  
4. Model training and evaluation  
5. Real-time inference  
6. Text-to-speech output  

---
## How It Works (Quick Flow)

1. The user performs a predefined hand gesture.
2. IMU sensors on the Arduino Nano 33 BLE Sense capture motion data.
3. Sensor data is processed and classified using an Edge Impulse ML model.
4. The predicted gesture label is sent to the laptop via Serial communication.
5. The laptop converts the label into speech using a text-to-speech engine.


## Technologies Used

- Python  
- Machine Learning (TensorFlow )  
- Arduino Nano 33 BLE Sense  
- Edge Impulse  
- pyttsx3 (Text-to-Speech)  
- NumPy
- Edge Impulse (model training & embedded inference SDK)


> MediaPipe is **not used** in this project.

## Repository Structure

```text
SIGN2SOUND_N3_Collectives/
├── README.md                 # Main documentation
├── requirements.txt          # Python dependencies
├── LICENSE                   # Apache 2.0 License
├── .gitignore                # Ignored files

├── data/
│   ├── README.md
│   ├── processed/
│   └── statistics.txt

├── preprocessing/
│   ├── preprocess.py
│   ├── augmentation.py
│   ├── extract_features.py
│   └── README.md

├── features/
│   ├── hand_landmarks.py
│   └── README.md

├── models/
│   ├── model.py
│   ├── custom_layers.py
│   ├── loss.py
│   └── README.md

├── training/
│   ├── train.py
│   ├── config.yaml
│   ├── callbacks.py
│   ├── evaluate.py
│   └── README.md

├── inference/
│   ├── infer.py
│   ├── realtime_demo.py
│   ├── tts.py
│   ├── utils.py
│   └── README.md

├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_model_experiments.ipynb
│   ├── 03_results_visualization.ipynb
│   └── README.md

├── results/
│   ├── metrics.json
│   ├── confusion_matrix.png
│   ├── loss_curves.png
│   ├── accuracy_curves.png
│   ├── per_class_performance.csv
│   ├── training_log.txt
│   └── sample_outputs/

└── checkpoints/
    └── best_model.h5 / best_model.pth
```


## Installation and Setup

### Prerequisites
- Python 3.9 or higher
- Arduino IDE
- Arduino Nano 33 BLE Sense
- Edge Impulse account

  ## Arduino Setup

1. Install Arduino Nano 33 BLE board support in the Arduino IDE  
2. Install required Arduino libraries:
   - Arduino_LSM9DS1  
   - Edge Impulse Arduino SDK (exported from Edge Impulse)  
3. Upload the inference sketch to the Arduino Nano 33 BLE Sense  

---

## Running Gesture-to-Speech

1. Connect the Arduino board to the laptop via USB  
2. Run the text-to-speech inference script from the project directory:

python inference/tts.py

The system listens to serial output from the Arduino and converts recognized gestures into audible speech on the laptop.

---

## Dataset Description

The dataset consists of time-series IMU sensor data collected from the Arduino Nano 33 BLE Sense.

Number of gesture classes: 13  

Sensors used:
- Accelerometer (X, Y, Z)  
- Gyroscope (X, Y, Z)  

Data format:
- Sliding window time-series samples  

Labeling:
- Manual labeling during gesture collection  

The dataset is split into training and validation sets for model evaluation.

---

## Results and Performance

The trained model demonstrates reliable real-time gesture recognition.

Overall Accuracy: 86.4%  
Number of Gesture Classes: 13  
Dataset Split: 79% Training / 21% Validation  
Inference Type: Real-time edge inference  

---

## Confusion Matrix
The confusion matrix below illustrates the classification performance across all gesture classes.

Confusion Matrix (View):  
https://drive.google.com/file/d/1BwA3jR9bNNxmPlSy4YrFES1bZaymEi9Q/view?usp=sharing

---

## Limitations

- Performance may vary across different users  
- Limited gesture vocabulary  
- Requires consistent gesture execution  
- No visual (camera-based) context  
- Environmental noise may affect IMU readings  

---

## Future Work

- Expand gesture vocabulary  
- Improve user-independent recognition  
- Add multilingual text-to-speech support  
- Deploy on wearable hardware  
- Integrate with mobile or desktop applications  

---

## Team

Team Name: N³_Collectives  

Team Member 1 – Data Collection & Preprocessing  
Team Member 2 – Model Training & Evaluation  
Team Member 3 – Embedded Deployment & TTS Integration  

---

## Project Links

Demo Video with Explanation:  https://drive.google.com/file/d/1OCkZVKUHyec6vC-THRHv7V2qHljsEWga/view?usp=drivesdk


Project Report:  https://drive.google.com/file/d/1s0MnmNTeWPK1FlU3cYF-niKtg1ZYTdvb/view?usp=drivesdk

---

## License

This project is licensed under the Apache License 2.0.  
See the LICENSE file for more details.

---

## Acknowledgements

- Edge Impulse for embedded machine learning tools  
- Arduino for hardware support  
- Open-source Python libraries used in this project  


