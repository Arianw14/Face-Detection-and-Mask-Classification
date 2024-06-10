Files:
1)Link is provided for google colab notebook -> "link_to_colab_notebook".Use this to get my code and run it.
2)"submission.csv" has the classifications done for all images(0000.jpg-1800.jpg).

Code Overview:
The provided code is a Python script that performs the following tasks:
1. Mounts Google Drive in Google Colab.
2. Extracts a zip file (`dataset.zip`) from Google Drive containing image data.
3. Reads a CSV file (`train.csv`) containing image annotations (bounding box coordinates and class labels).
4. Concatenates annotations for images labeled as "face_with_mask" and "face_no_mask".
5. Loads and preprocesses images based on the annotations.
6. Augments the image data using `ImageDataGenerator` from TensorFlow Keras.
7. Splits the dataset into training and validation sets.
8. Builds a convolutional neural network (CNN) model using the Xception architecture for binary classification of images into "face_with_mask" and "face_no_mask" classes.
9. Trains the CNN model on the training data with early stopping and learning rate reduction callbacks.
10. Saves the best-performing model based on validation accuracy.
11. Defines functions to:
   - Load the saved model.
   - Detect faces in images using YOLOv3 face detector.
   - Classify faces as wearing a mask or not using the trained CNN model.
   - Process images for submission, including face detection and classification.
12. Processes images from a CSV file (`submission.csv`) for submission, detecting faces and predicting mask wearing based on the trained models.
13. Saves the processed data to a new CSV file (`submission.csv`).

Key Components:
- Data Loading and Preprocessing:
  - Image data is loaded from the extracted dataset and resized to a standard size (224x224 pixels).
  - Image annotations are read from a CSV file and concatenated for faces with and without masks.
  - Images are augmented using `ImageDataGenerator` to increase the dataset size and improve model generalization.

- Model Training:
  - The Xception architecture is used as the base model for transfer learning.
  - The model is compiled with the Adam optimizer and binary cross-entropy loss for binary classification.
  - Training is performed with early stopping and learning rate reduction callbacks to prevent overfitting.

- Face Detection and Mask Classification:
  - YOLOv3 face detector is used to detect faces in images.
  - The trained CNN model is used to classify detected faces as wearing a mask or not.

- Submission Data Processing:
  - Images are processed for submission by detecting faces and predicting mask wearing based on the trained models.
  - The processed data is saved to a CSV file for submission.