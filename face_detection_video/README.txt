How to execute:

1) docker build -t face_detection_app . (run this in the directory)

2) docker run -v /path/to/host/directory:/app/output face_detection_app


Code Overview:
The provided code is a Python script that performs the following tasks:
1. Defines a function `classify_face` to classify a detected face as wearing a mask or not using a trained model.
2. Defines a class `YOLOv8_face` for face detection using YOLOv8 architecture.
3. Defines a function `process_video` to process input videos by detecting faces, tracking them, and classifying mask-wearing using the previously defined functions and models.
4. Loads a pre-trained mask detection model (`face_detection_best_model.keras`) using Keras.
5. Calls the `process_video` function to process multiple input videos (`Test_video1.mp4`, `Test_video2.mp4`, `Test_video3.mp4`) and save the output videos with detected faces and mask classification.

 Key Components:
- `classify_face` Function:
  - Parameters:
    - `frame`: Input frame containing the detected face.
    - `box`: Bounding box coordinates of the detected face.
    - `model`: Trained model for mask detection.
  - Returns:
    - Index indicating mask (1) or no mask (0).
  - This function takes a frame and the bounding box of a detected face, preprocesses it, predicts whether the person is wearing a mask or not using the provided model, and returns the prediction.

- `YOLOv8_face` Class:
  - Parameters:
    - `path`: Path to the YOLOv8 model file.
    - `conf_thres`: Confidence threshold for face detection.
    - `iou_thres`: Intersection over Union (IoU) threshold.
  - Methods:
    - `detect`: Detects faces in an input image.
  - This class encapsulates the functionality for face detection using the YOLOv8 architecture. It includes methods for model initialization, anchor generation, post-processing of predictions, and face detection.

- `process_video` Function:
  - Parameters:
    - `input_path`: Path to the input video file.
    - `output_path`: Path to save the output video.
    - `mask_model`: Trained model for mask detection.
    - `face_model_path`: Path to the YOLOv8 face detection model.
    - `conf_threshold`: Confidence threshold for face detection.
    - `nms_threshold`: Non-maximum suppression threshold.
    - `check_interval`: Interval for checking face detection.
    - `distance_threshold`: Threshold for tracking distance.
  - This function processes the input video by detecting faces, tracking them, classifying mask-wearing, and saving the output video with annotations.