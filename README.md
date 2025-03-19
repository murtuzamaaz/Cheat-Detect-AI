# Cheating Surveillance System

## Overview
The **Cheating Surveillance System** is designed to detect cheating during **Online Interviews/Exams** by monitoring head and pupil movements and identifying unauthorized mobile phone usage. This system integrates **facial landmark detection** using **dlib's Shape Predictor 68** and **object detection** using **YOLOv8 and YOLOv12**, trained on a cellphone detection dataset from **Roboflow**.

## Features
- **Head and Pupil Movement Detection:** Uses `dlib`'s **Shape Predictor 68** to track facial landmarks and detect suspicious gaze patterns.
- **Mobile Phone Detection:** Utilizes a **YOLOv12 model** trained on the **Roboflow Cellphone Detection Dataset** to detect mobile phones in real-time.
- **Real-Time Monitoring:** Processes live video feeds for instant analysis and detection.
- **Alert System:** Flags potential cheating behavior, such as excessive head or pupil movement in the **left, right, up, or down direction** for longer than the allowed time.

## Technologies Used
- **Python 3.8+**
- **OpenCV** (for video processing)
- **dlib** (for facial landmark detection)
- **YOLO** (for object detection)
- **Roboflow Dataset** (for training the mobile detection model)

## Folder Structure
```
cheating-surveillance/
│── models/                 # Contains trained YOLO weights and shape predictor model  
│   ├── best_yolov8.pt
│   ├── best_yolov12.pt
│   ├── shape_predictor_68_face_landmarks.dat
│── log/                    # Screenshots
│── main.py                 # Entry point for real-time detection
│── requirements.txt        # Required dependencies
│── README.md               # Project documentation
│── head_pose.py            # Head movement detection
│── eye_movement.py         # Gaze Detection
│── mobile_detection.py     # Mobile detection
│── Demo_vid/               # Folder containing demo videos
```

## Installation
### Prerequisites
Ensure you have the following installed:
- **Python 3.8+**
- **OpenCV** (`pip install opencv-python`)
- **dlib** (`pip install dlib`)
- **torch** (for YOLO) (`pip install torch torchvision torchaudio`)
- **roboflow** (for dataset access) (`pip install roboflow`)

### Setup
#### 1. Clone the repository:
```sh
git clone https://github.com/Sania-hasann/Cheating-Surveillance-System.git
cd Cheating-Surveillance-System
```
#### 2. Install dependencies:
```sh
pip install -r requirements.txt
```
#### 3. Download the Shape Predictor 68 model:
```sh
wget http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2
bzip2 -d shape_predictor_68_face_landmarks.dat.bz2
```
#### 4. Set up the YOLO model:
- Ensure your YOLO model is trained on the **Roboflow Cellphone Detection Dataset**.
- Download the trained YOLO weights and place them in the `models/` directory.

## Usage
### Running the Surveillance System
To start real-time monitoring, run:
```sh
python main.py
```

### How It Works
1. **Facial Landmark Detection:** Detects and tracks head movements and pupil direction.
2. **YOLO-based Object Detection:** Identifies mobile phones in the video feed.
3. **Cheating Behavior Analysis:** Flags abnormal behavior such as frequent head turning or gaze shifts.

## Troubleshooting
### 1. OpenCV `cv2.imshow` Error:
**Error Message:**
```
cv2.error: OpenCV(4.10.0) ... error: (-2:Unspecified error) The function is not implemented...
```
**Solution:**
- If you are on **Windows**, use the following before `cv2.imshow()`:
  ```python
  cv2.namedWindow("Combined Detection", cv2.WINDOW_NORMAL)
  ```
- If the issue persists, uninstall and reinstall OpenCV:
  ```sh
  pip uninstall opencv-python opencv-python-headless
  pip install opencv-python
  ```

### 2. dlib Version Issue:
**Error Message:** `pip install dlib==19.22.99` not found.

**Solution:**
- Install a valid version (`19.24.2` is recommended):
  ```sh
  pip install dlib==19.24.2
  ```

## Demo Videos
- **Gaze Detection**
- **Head Movement Detection**
- **Mobile Phone Detection**

## Dataset
The **mobile phone detection model** is trained on the **Roboflow Cellphone Detection Dataset**. You can access it here: [Roboflow Cellphone Dataset](https://roboflow.com/)

## Contributing
Contributions are welcome! Follow these steps:
1. **Fork the repository.**
2. **Create a new branch:**
   ```sh
   git checkout -b feature-branch
   ```
3. **Commit your changes:**
   ```sh
   git commit -m "Add new feature"
   ```
4. **Push to the branch:**
   ```sh
   git push origin feature-branch
   ```
5. **Open a Pull Request.**

## License
This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- **dlib**
- **OpenCV**
- **YOLO**
- **Roboflow** for dataset support

