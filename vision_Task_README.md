## Outdoor Smoke Detection using YOLOv8

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
