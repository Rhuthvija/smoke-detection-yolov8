# internship_inML
This repository contains my work during my ML internship.

📂 Folder Overview
/images/ → Contains screenshots and reference visuals.
/notebooks/ → Will include Python notebooks or scripts used during my internship.
README.md → This document explains the structure and purpose of the repository.
🧠 Project Summary
During this internship, I explored the following:

# task 1: Object Detection and Segmentation using YOLOv8

This repository contains my work for the **Machine Learning Internship** project — focusing on **object detection and segmentation** using the **YOLOv8** model from Ultralytics.

---

## 🚀 Project Overview

The goal of this project is to perform **object detection and segmentation** on real-world images using the YOLOv8 model.

### Tasks Completed:

* Installed and configured the YOLOv8 environment
* Ran object detection on sample images (`classroom.jpg`, `office.jpg`)
* Visualized bounding boxes and segmentation masks
* Compared detection vs segmentation results

---

## 🧩 Tools & Libraries

| Tool                   | Purpose                         |
| ---------------------- | ------------------------------- |
| **Python 3.x**         | Programming language            |
| **Ultralytics YOLOv8** | Object detection & segmentation |
| **OpenCV**             | Image processing                |
| **Matplotlib**         | Visualization                   |
| **NumPy**              | Array operations                |

---

## 📁 Repository Structure

```
internship_inML/
│
├── code/
│   ├── detection_classroom.py
│   ├── segmentation_office.py
│
├── images/
│   ├── classroom.jpg
│   ├── office.jpg
│   └── results/
│       ├── classroom_detected.jpg
│       ├── office_segmented.jpg
│
├── requirements.txt
└── README.md
```

---

## 📷 Sample Results

| Image                  
| ---------------------- 
| classroom_detected.jpg 
| office_segmented.jpg   
---

## 🧠 Next Steps

* Experiment with different YOLOv8 models (e.g., `yolov8m`, `yolov8l`)
* Evaluate performance using metrics like Precision, Recall, and mAP
* Try real-time detection using webcam feed

---




## task 2:  Video Detection using YOLOv8

In this section, we take a short video clip and perform object detection frame-by-frame.

### 🧩 Step 1: Extract frames from the video

We use **FFmpeg** to split a video into sequential images:

```bash
ffmpeg -i input.mp4 frames/frame_%04d.jpg
```
### 🎥 Video Detection Results
- [Input video (Google Drive link)]([https://drive.google.com/...](https://drive.google.com/file/d/1hm5oYblcNJ7Kw0asFL1eLytWiEI98Os3/view?usp=drive_link))
- [Processed output video (Google Drive link)](https://drive.google.com/file/d/1GHijquTaxzF1daGmt_42MJWdRRpEcneJ/view?usp=drive_link)

* `input.mp4` → your video file
* `frames/frame_%04d.jpg` → output folder and image pattern

### 🧠 Step 2: Run YOLOv8 object detection on all frames

```bash
yolo detect predict model=yolov8n.pt source="frames/" save=True
```

This generates processed images (with bounding boxes) inside the `runs/detect/predict/` folder.

### 🎞️ Step 3: Combine processed frames back into a video

We use FFmpeg again to stitch them together:

```bash
ffmpeg -framerate 24 -i runs/detect/predict/frame_%04d.jpg -c:v libx264 -pix_fmt yuv420p output.mp4
```

* `output.mp4` will be your final detected video
* You can play it using any media player

### 🧾 Output

* **Input video:** `input.mp4`
* **Processed video:** `output.mp4`

This demonstrates how YOLOv8 can handle not just static images, but dynamic video streams by processing frames in sequence.



## vision task: Outdoor Smoke Detection using YOLOv8

### Problem Statement
Air pollution due to outdoor smoke from factories, vehicles, and wildfires poses serious risks to public health and the environment.  
The objective of this project is to automatically detect outdoor smoke in video streams using computer vision, with minimal human intervention.

### Approach
1. Collected real-world outdoor smoke videos (factory emissions, vehicular smoke, wildfire smoke).
2. Extracted diverse frames from videos using FFmpeg.
3. Annotated smoke regions manually using Label Studio.
4. Created a custom YOLO-format dataset (train/validation split).
5. Performed transfer learning using a pre-trained YOLOv8 model.
6. Ran object detection on multiple unseen videos.
7. Merged all processed outputs into a single demonstration video.

### Tools & Technologies
- Python
- YOLOv8 (Ultralytics)
- Label Studio
- FFmpeg
- OpenCV
- GitHub

### Results
The trained model is able to detect outdoor smoke across different scenarios including industrial areas, vehicles, and wildfires.  
The final output video demonstrates consistent smoke detection across multiple real-world clips.

### Output
- Final merged video: `final_output_smoke_detection.mp4`

*Created and maintained by [Rhuthvija](https://github.com/Rhuthvija)* ✨


