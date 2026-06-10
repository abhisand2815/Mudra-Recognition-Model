# Sattriya Mudra Recognition System

A real-time hand gesture recognition system for identifying classical hand gestures (mudras) from the Sattriya dance tradition of Assam, India. The system uses computer vision and hand landmark detection to classify single-hand mudras through a live webcam feed.

---

## Overview

Sattriya is one of the eight classical dance forms of India, originating from the Vaishnavite monasteries of Assam. Central to its expressive vocabulary are *mudras* — codified hand gestures that convey specific meanings, emotions, characters, and narrative elements. This project applies real-time pose estimation to recognize a curated set of Sattriya mudras, overlaying gesture names, confidence scores, and descriptive text directly onto the video stream.

---

## Features

- Real-time detection and classification of Sattriya hand mudras via webcam
- Recognition of 27 distinct mudras including Pataka, Tripataka, Alapadma, Mushti, Simhamukha, and more
- Confidence score display for each recognized gesture
- On-screen description panel providing the semantic meaning of each detected mudra
- Landmark overlay using MediaPipe hand tracking
- Support for both left and right hand orientation

---

## Recognized Mudras

| Mudra | Meaning |
|---|---|
| Pataka | Flag — blessings, a forest |
| Tripataka | Three parts of a flag — crowns, trees |
| Ardhapataka | Half-flag — a knife, the number two |
| Ardhachandra | Half-moon — the sky, waist |
| Alapadma | Full-blown lotus — beauty |
| Chandrakala | Crescent moon — moon on Shiva's head |
| Mukula | Bud — a lotus bud, act of eating |
| Kataka Mukha | Opening of a bracelet — plucking flowers |
| Simhamukha | Lion's face — courage, a lion |
| Sandamsa | Pincers — grasping, plucking |
| Chatura | Clever/square — musk, cleverness |
| Suchimukha | Needle face — pointing |
| Shikara | Peak — determination, a bow |
| Mushti | Fist — steadiness, combat |
| Trishula | Trident — Lord Shiva's weapon |
| Arala | Bent — drinking nectar, violent wind |
| Bhramara | Bee — a bee, yoga |
| Mrigashirsha | Deer's head — a deer, cheeks |
| Padmakosha | Lotus bud — a fruit, a ball |
| Hamsasya | Swan's beak — softness, tying a knot |
| Mayura | Peacock — a peacock |
| Kartarimukha | Scissor's face — scissors, separation |
| Sarpashirsha | Serpent's head — a cobra hood |
| Hamsapaksha | Swan's wing — a bridge, veil |
| Kapittha | Grasping cymbals, worship of Lakshmi and Sarasvati |
| Kangula | Lakuca fruit, bell, a bird |
| Shukatunda | Parrot's beak — a hook, shooting an arrow |
| Tamrachuda | Cock’s crest — a rooster, pride, alertness |

---

## Requirements

### System Dependencies

- Python 3.8 or higher
- A functioning webcam

### Python Libraries

```
opencv-python
mediapipe
numpy
```

Install all dependencies with:

```bash
pip install opencv-python mediapipe numpy
```

---

## Usage

- Launch the script. A webcam window titled **Mudra Identifier** will open.
- Hold one hand in front of the camera and form a mudra.
- The detected mudra name appears at the top left of the frame in red.
- A confidence percentage is shown below the name.
- A translucent description panel at the bottom of the frame displays the semantic meaning of the detected gesture.
- Press **Q** to quit the application.

**Notes:**
- Ensure adequate, even lighting for best detection accuracy.
- The system is optimized for single-hand detection. Keep the performing hand clearly visible and unobstructed.
- A neutral, non-patterned background improves landmark tracking reliability.

---

## How It Works

### Hand Landmark Detection

MediaPipe Hands is used to detect and track 21 three-dimensional landmarks on the hand in each frame. These landmarks correspond to joints and key points across the palm and all five fingers.

### Feature Extraction

From the raw landmarks, the following geometric features are computed per frame:

- **Finger state** — whether each finger is extended or folded, determined by comparing tip and intermediate joint positions
- **Inter-landmark distances** — Euclidean distances between key points such as fingertips and the thumb
- **Joint angles** — angles at specific joints (e.g., PIP joint of the index finger) to distinguish between straight and bent postures
- **Hand size normalization** — distances are evaluated relative to a baseline hand size (wrist to mid-palm) to ensure scale invariance

### Classification

A rule-based classifier maps the extracted features to mudra categories. Each rule encodes the anatomical finger configuration and spatial relationships that characterize a specific mudra. Ambiguous gestures (such as Tamrachuda vs. Chandrakala) are resolved using additional joint angle measurements.

### Confidence Scoring

A raw confidence value is assigned by the classifier based on how cleanly a gesture matches its defining criteria. This is scaled to a display range of 92–100% for recognized mudras to reflect the inherent variability of real-world hand poses.

---

## Project Structure

```
sattriya-mudra-recognition/
|
|-- mudra_recognition.py        # Main application script
|-- README.md                   # Project documentation
```

---

## Known Limitations

- The system currently supports single-hand detection only. Dual-hand mudras (Samyukta Hastas) are not yet implemented.
- Certain mudras with subtle distinctions (e.g., Hamsasya vs. Sandamsa) may require precise hand positioning for reliable differentiation.
- Detection accuracy may degrade under low-light conditions or when the hand is partially occluded.
- The classifier does not account for wrist orientation or arm posture, which carry additional meaning in the full Sattriya vocabulary.

---

## Future Work

- Extend support to Samyukta (combined two-hand) mudras
- Integrate temporal gesture sequencing for dance phrase recognition
- Develop a training data pipeline for a machine learning-based classifier to replace rule-based logic
- Add support for recording and annotating gesture sequences
- Build a web-based interface for accessibility without a local Python environment

---

## References

- Sangeet Natak Akademi — Sattriya Dance Documentation
- Abhinaya Darpana (Mirror of Gesture) — Nandikesvara
- MediaPipe Hands: [https://mediapipe.dev](https://mediapipe.dev)
- OpenCV Documentation: [https://docs.opencv.org](https://docs.opencv.org)

---

## License

This project is released for academic and educational purposes. Please cite this repository if you use it in research related to Indian classical dance or gesture recognition.
