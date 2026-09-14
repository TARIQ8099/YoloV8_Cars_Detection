# YOLOv8 Car Detector

A YOLOv8 video detection script. It draws bounding boxes on a video, logs every detection to a CSV file, and saves the annotated output as a new video.

![Python](https://img.shields.io/badge/python-3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/model-YOLOv8-orange)
![License](https://img.shields.io/badge/license-MIT-green)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Output Files](#output-files)
- [Project Structure](#project-structure)
- [Limitations](#limitations)
- [Roadmap](#roadmap)
- [License](#license)

## Overview

The script reads a video frame by frame, runs each frame through a YOLOv8 model, and draws the resulting bounding boxes on screen. It shows live FPS and object count on the video, writes an annotated copy to disk, and logs each individual detection to a CSV file.

The model detects standard COCO classes, so it works on any footage containing common objects. The car footage in the example is just the test case.

## Features

- Live annotated preview while the video processes
- FPS and object count displayed on the video feed
- CSV log of every detection: frame number, class, confidence
- Annotated video saved to disk
- Summary report printed at the end: total frames, total objects, per-class counts

## Installation

Requires Python 3.8 or later.

```bash
git clone https://github.com/<your-username>/yolov8-car-detector.git
cd yolov8-car-detector
pip install ultralytics opencv-python
```

The YOLOv8 weights download automatically the first time you run the script.

## Usage

Put your input video in the project folder, or point `VIDEO_PATH` at it, then run:

```bash
python YoloV8_cars_detection.py
```

A preview window opens and shows detections as they happen. Press `q` to stop early.

When the run finishes, you get:
- `output.mp4`, the annotated video
- `detections.csv`, the detection log
- A summary printed in the terminal

## Configuration

Edit these values at the top of the script:

| Setting | Description | Default |
|---|---|---|
| `MODEL_PATH` | YOLOv8 weights file | `yolov8n.pt` |
| `VIDEO_PATH` | Input video | `cars.mp4` |
| `OUTPUT_VIDEO` | Output video filename | `output.mp4` |
| `CONFIDENCE` | Minimum confidence to count a detection | `0.5` |

A larger model (`s`, `m`, `l`, `x`) gives better accuracy at the cost of speed.

## Output Files

| File | Contents |
|---|---|
| `output.mp4` | Video with boxes, FPS, and object count drawn on |
| `detections.csv` | One row per detection: frame, class, confidence |
| Terminal output | Total frames, total objects, count per class |

## Project Structure

```
yolov8-car-detector/
├── YoloV8_cars_detection.py
├── cars.mp4          (not included)
├── output.mp4        (generated)
├── detections.csv    (generated)
└── README.md
```

## Limitations

- Detects only the object classes YOLOv8 was trained on (standard COCO), no fine-grained vehicle types.
- The FPS number reflects processing speed, not real-time playback speed.
- The preview window needs a display. Remove `cv2.imshow` for headless use.

## Roadmap

- [ ] Command-line arguments for video path, model, and confidence
- [ ] Headless mode for servers
- [ ] Object tracking for unique vehicle counts
- [ ] Batch processing for multiple videos
- [ ] Configurable overlay styling

## License

For educational and personal use.
