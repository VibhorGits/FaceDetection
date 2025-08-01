# Face Liveness Detection

This project is a real-time face liveness detection system designed to distinguish between live faces and spoofed faces (e.g., from a photo or video). It uses a YOLOv8 model trained to classify faces as either "real" or "fake," providing an essential layer of security for facial recognition systems.

## Table of Contents
- [Directory Structure](#directory-structure)
- [Project Title and Description](#face-liveness-detection)
- [Table of Contents](#table-of-contents)
- [Installation Instructions](#installation-instructions)
- [Usage Guide](#usage-guide)
- [Features](#features)

## Directory Structure

```
├── main.py
├── train.py
├── splitData.py
├── dataCollection.py
├── Dataset/
│   └── SplitData/
│       └── dataOffline.yaml
├── runs/
│   └── detect/
│       └── train/
│           ├── results.csv
│           └── args.yaml
├── Testing Scripts/
│   ├── yoloTest.py
│   └── faceDetectorTest.py
```

## Installation Instructions

To get this project up and running, you'll need to have Python and pip installed. Then, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/face-liveness-detection.git](https://github.com/your-username/face-liveness-detection.git)
    cd face-liveness-detection
    ```

2.  **Install the required dependencies:**
    ```bash
    pip install opencv-python cvzone ultralytics
    ```

## Usage Guide

This project is divided into several scripts, each responsible for a specific part of the pipeline, from data collection to real-time detection.

### 1. Data Collection (`dataCollection.py`)

This script is used to collect face images for training the model. You can collect images of "real" faces (by pointing the camera at yourself) and "fake" faces (by pointing the camera at a photo or video of a face).

-   **To collect images of fake faces**, run the script with `classID = 0`.
-   **To collect images of real faces**, change `classID` to `1`.

```python
# In dataCollection.py
classID = 0  # 0 for fake, 1 for real
```
Run the script from your terminal:
```bash
python dataCollection.py
```

### 2. Splitting the Data (`splitData.py`)

After collecting the data, this script will split it into training, validation, and test sets. It will also create a `dataOffline.yaml` file, which is required for training the YOLOv8 model.

Run the script from your terminal:
```bash
python splitData.py
```

### 3. Training the Model (`train.py`)

This script trains the YOLOv8 model on the dataset you've prepared. The trained model will be saved in the `runs/detect/train/` directory.

Run the script from your terminal:
```bash
python train.py
```

### 4. Real-Time Liveness Detection (`main.py`)

This is the main script that runs the real-time face liveness detection. It uses the trained model to classify faces as "real" or "fake" and displays the results on the screen.

Run the script from your terminal:
```bash
python main.py
```

## Features

-   **Real-Time Detection:** The system processes video streams in real-time to detect and classify faces.
-   **High Accuracy:** Utilizes the YOLOv8 model, known for its speed and accuracy in object detection tasks.
-   **Complete Pipeline:** Provides a full pipeline from collecting data to training and deploying the model.
-   **Spoofing Prevention:** Designed to prevent spoofing attacks in facial recognition systems, enhancing security.
