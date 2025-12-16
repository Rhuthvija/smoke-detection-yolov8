## Outdoor Smoke Detection using YOLOv8

### Problem Statement
Air pollution due to outdoor smoke from factories, vehicles, and wildfires poses serious risks to public health and the environment.  
The objective of this project is to automatically detect outdoor smoke in video streams using computer vision, with minimal human intervention.

Approach
Collected real-world outdoor smoke videos (factory emissions, vehicular smoke, wildfire smoke).
Extracted diverse frames from videos using FFmpeg.
Annotated smoke regions manually using Label Studio.
Created a custom YOLO-format dataset (train/validation split).
Performed transfer learning using a pre-trained YOLOv8 model.
Ran object detection on multiple unseen videos.
Merged all processed outputs into a single demonstration video.

Frame Extraction
Used FFmpeg to extract frames from videos. Special care was taken to avoid near-duplicate frames (high FPS causes overfitting). Selected diverse frames manually to improve generalization.

Annotation (Major Challenge)
Installed and used Label Studio for manual annotation. Labeled smoke regions using bounding boxes. One major challenge faced was: Configuring Label Studio to correctly load local image paths Avoiding over-annotation of visually similar frames Final dataset consisted of ~90+ carefully annotated images.

Dataset Preparation
Converted annotations into YOLO format. Organized dataset into: images/train, images/val labels/train, labels/val Created a custom data.yaml file for training.

Repository Structure (Explanation)
├── data.yaml ├── yolov8n.pt ├── final_output_smoke_detection.mp4 ├── runs/ │ └── detect/ │ └── train6/ │ └── weights/ │ ├── best.pt │ └── last.pt └── README.md

File Explanations
data.yaml Defines dataset paths, number of classes, and class names for YOLO training. 
yolov8n.pt Pre-trained YOLOv8 model used as the base for transfer learning. 
final_output_smoke_detection.mp4 Merged output video demonstrating smoke detection.

⚠️ Note on Missing Files (Important) 
Due to GitHub file size limitations, the following folders are not uploaded: 
images/ 
labels/ 
However, the complete dataset was used locally for: Annotation Training Validation and is fully reflected in the final trained model and output video.

Tools & Technologies
Python
YOLOv8 (Ultralytics)
Label Studio
FFmpeg
OpenCV
GitHub

Results
The final output video demonstrates consistent smoke detection across multiple real-world clips.

Key Learnings
Dataset quality is more important than dataset size. 
Annotation is the most time-consuming and critical step. 
Debugging dataset paths and training configurations is a core ML skill. 
End-to-end pipelines are significantly harder than running pre-trained demos.

Output
Final merged video: final_output_smoke_detection.mp4
Created and maintained by Rhuthvija ✨
