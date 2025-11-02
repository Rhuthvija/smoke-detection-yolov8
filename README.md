# internship_inML
This repository contains my work during my ML internship.

📂 Folder Overview
/images/ → Contains screenshots and reference visuals.
/notebooks/ → Will include Python notebooks or scripts used during my internship.
README.md → This document explains the structure and purpose of the repository.
🧠 Project Summary
During this internship, I explored the following:

Basics of Machine Learning
Understanding YOLO and object detection
Setting up local and remote repositories with Git and GitHub
Working with VS Code and terminal commands
🖥️ My Setup
Device: MacBook Air M4
Tools Used: VS Code, Git, Python
Environment Path: /Users/ruby/internship_inML
📸 Visuals
Below are a few images from my internship progress:

Classroom Office

Save the file (⌘ + S).
Run these commands in your VS Code terminal:
git add README.md
git commit -m "Added README description and images"
git push origin main


---

## 🎥 Video Detection using YOLOv8

In this section, we take a short video clip and perform object detection frame-by-frame.

### 🧩 Step 1: Extract frames from the video

We use **FFmpeg** to split a video into sequential images:

```bash
ffmpeg -i input.mp4 frames/frame_%04d.jpg
```

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


