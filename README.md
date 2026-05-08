# Bowling Score Detection from Video Using Computer Vision 🎳

A deep learning and computer vision system for detecting, tracking, and scoring bowling pins automatically from recorded bowling videos using YOLOv8 and OpenCV.

---

# 📌 Project Overview

This project was developed as part of the DSAI 352 Final Project.

The system processes a recorded bowling video and automatically:

- Detects bowling pins using a fine-tuned YOLOv8 model
- Tracks pin positions across video frames
- Detects when a pin falls
- Records the exact timestamp of the fall
- Maintains pin identity during the game
- Generates an annotated output video
- Displays the final score and game duration

The project simulates a simplified bowling game scenario with multiple throws recorded in a single video.

---

# 🎯 Objectives

The main goals of this project are:

- Apply deep learning to real-world video understanding tasks
- Build a custom object detection pipeline
- Perform object tracking across frames
- Detect state transitions (standing → fallen)
- Generate annotated visual outputs automatically

---

# 🧠 Technologies Used

- Python
- OpenCV
- YOLOv8
- Ultralytics
- Roboflow
- NumPy
- Google Colab

---

# 🏗️ System Pipeline

The system follows the following pipeline:

1. Input bowling video is loaded
2. YOLOv8 detects bowling pins frame-by-frame
3. Duplicate detections are filtered using Non-Maximum Suppression (NMS)
4. Pins are assigned stable identities using centroid matching
5. The system monitors each pin state:
   - Standing
   - Fallen
6. A fall is confirmed using temporal consistency checks
7. Fallen pins are marked visually on the video
8. Timestamps are recorded for every fallen pin
9. Final statistics are displayed at the end of the video

---

# 📂 Dataset

The dataset was collected and managed using Roboflow.

Dataset includes:
- Bowling pin images
- Standing and fallen pin states
- YOLO annotation format

The dataset was automatically downloaded using the Roboflow API.

---

# 🤖 Model Training

The project uses transfer learning with a pretrained YOLOv8 nano model.

## Training Configuration

| Parameter | Value |
|---|---|
| Model | YOLOv8n |
| Epochs | 50 |
| Image Size | 640 |
| Batch Size | 16 |
| Framework | Ultralytics |
| Training Environment | Google Colab |

The model was fine-tuned on a custom bowling pin dataset.

---

# 🧩 Pin Tracking Logic

To maintain stable pin identities across frames, the system uses:

- Centroid-based matching
- Distance thresholding
- Sliding temporal windows
- Consecutive-frame fall confirmation

This improves robustness against:
- Motion blur
- Occlusion
- Missed detections
- Fast-moving pins

---

# 📸 Detection Results

## Bowling Pin Detection

<!-- ADD DETECTION IMAGE HERE -->

```markdown
![Detection Result](results/detection.png)
```

---

# 🎥 Output Video

The system generates an annotated output video containing:

- Pin markers
- Fall timestamps
- Real-time score updates
- Final game summary

Example overlays:
- `Pin 2 fell @ 6.4s`
- `Pins down: 3/5`

---

# 🧮 Fall Detection Strategy

A pin is considered fallen when:

- The model repeatedly classifies it as fallen across consecutive frames
OR
- The pin disappears from view for a sustained period

The system uses:
- Consecutive detection confirmation
- Sliding window voting
- Missing-frame tolerance

to reduce false positives.

---

# 📊 Features

✅ Bowling pin detection  
✅ Pin tracking  
✅ Fall timestamp recording  
✅ Annotated video rendering  
✅ Final score calculation  
✅ Deep learning-based detection  
✅ Custom-trained YOLOv8 model  

---

# 📁 Project Structure

```text
Bowling-Score-Detection/
│
├── dataset/
├── models/
│   └── best.pt
├── videos/
│   ├── input/
│   └── output/
├── notebooks/
│   └── CV_Final_Project.ipynb
├── results/
│   ├── detection.png
│   └── output_frame.png
├── requirements.txt
├── README.md
└── report.pdf
```

---

# ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/Bowling-Score-Detection.git
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# ▶️ Run the Project

Train model:

```python
model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640,
    batch=16
)
```

Run inference:

```python
python detect.py
```

---

# 📈 Evaluation

The trained model was evaluated using validation metrics provided by YOLOv8.

Evaluation includes:
- Detection confidence
- Localization accuracy
- Validation performance

---

# 💡 Challenges

Some challenges faced during development:

- Motion blur
- Pin overlap
- Partial occlusion
- Fast pin movement
- False duplicate detections
- Maintaining stable identities

These were handled using:
- Non-Maximum Suppression
- Temporal smoothing
- Distance-based matching
- Sliding windows

---

# 🚀 Future Improvements

Possible future enhancements:

- Real-time bowling analysis
- Ball trajectory tracking
- Strike/spare recognition
- Multi-camera support
- Full ten-pin bowling support
- Advanced tracking algorithms (SORT/DeepSORT)

---

# 📄 Project Requirements Satisfaction

This project satisfies the DSAI 352 Final Project requirements by:

✅ Using a fine-tuned deep learning model  
✅ Processing recorded bowling videos  
✅ Detecting and tracking pins  
✅ Identifying fallen pins  
✅ Recording timestamps  
✅ Generating annotated output videos  
✅ Displaying final scores  


# 📜 License

This project is licensed under the MIT License.

---

# ⭐ Acknowledgements

Special thanks to:

- Ultralytics YOLOv8
- Roboflow
- OpenCV
- Google Colab

for providing the tools and frameworks used in this project.
