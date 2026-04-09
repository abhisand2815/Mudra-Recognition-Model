# Sattriya Folk Dance Mudra Recognition Model

## Overview
This project presents a real-time hand gesture recognition system designed specifically for identifying Sattriya dance mudras using computer vision techniques. The system uses MediaPipe Hand Tracking and a rule-based classification approach to detect and interpret various mudras through live webcam input.

The objective of this project is to digitally preserve and analyze traditional Sattriya dance gestures using modern AI and image processing technologies.

---

## Features
- Real-time hand tracking using webcam
- Detection of multiple Sattriya mudras
- Confidence score for each detected mudra
- Rule-based classification using geometric calculations
- On-screen description of each mudra
- Lightweight and fast (no heavy machine learning model required)

---

## Supported Mudras
The system can recognize multiple mudras including:
Mukula, Kataka Mukha, Alapadma, Simhamukha, Chandrakala, Pataka, Tripataka, Arala, Shikara, Trishula, Mrigashirsha, Hamsasya, Kapittha, Kangula, Sarpashirsha, Hamsapaksha, Mushti and more.

---

## Technologies Used
- Python
- OpenCV (for image processing)
- MediaPipe (for hand landmark detection)
- NumPy (for numerical computation)
- Math module (for geometric calculations)

---

## Working Principle

1. Hand Detection  
MediaPipe detects 21 hand landmarks in real-time.

2. Feature Extraction  
Distances between key landmarks are calculated, finger states (up/down) are identified, and angles between joints are computed.

3. Mudra Classification  
Rule-based logic compares geometric patterns and identifies the mudra.

4. Output Display  
Mudra name, confidence score, and description are displayed on screen.

---

## Project Structure
├── mudra.py  
├── README.md  

---

## Installation and Setup

### Clone the repository
git clone https://github.com/your-username/mudra-recognition.git  
cd mudra-recognition  

### Install dependencies
pip install opencv-python mediapipe numpy  

### Run the project
python mudra.py  

---

## Usage
- Run the script  
- Show your hand in front of the webcam  
- Perform a Sattriya mudra  
- The system will detect the gesture and display:
  - Mudra name  
  - Confidence score  
  - Description  

Press 'q' to exit.

---

## Example Output
Mudra Name: Pataka  
Confidence: 95%  
Description: Represents blessings or the start of a dance  

---

## Key Highlights
- Does not rely on deep learning models  
- Uses geometry-based reasoning (distances and angles)  
- Works in real-time  
- Easily extendable for more mudras  

---

## Future Improvements
- Integrate deep learning for improved accuracy  
- Mobile application deployment  
- Support for more classical dance forms  
- Dataset-based training and evaluation  
- Multi-hand gesture recognition  

---

## Contribution
Contributions are welcome. Feel free to fork the repository and improve the project.

---

## License
This project is open-source and available under the MIT License.

---

## Author
Abhimanyu Singh
