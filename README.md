# Silkworm Disease Detection using MobileNetV2

## 1. Project Overview

The Silkworm Disease Detection Model is a deep learning-based image classification system developed to identify different silkworm diseases using image input.

The model uses MobileNetV2 transfer learning to classify silkworm images into five categories: Healthy, Pebrine, Flacherie, Overlap and Grasserie.

This project is developed as part of **SeriGuard AI**, an intelligent silkworm monitoring system that aims to integrate AI-based disease detection with IoT-based environmental monitoring.

## 2. Objectives

- Automatically identify silkworm diseases using images.
- Enable early detection of infected silkworms.
- Reduce manual inspection efforts.
- Improve disease monitoring in sericulture.
- Support integration with IoT-based silkworm monitoring systems.

## 3. Technologies Used

- Python
- TensorFlow
- Keras
- MobileNetV2
- OpenCV
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab

## 4. Dataset Description

The model uses the Mendeley Silkworm Dataset.

It contains five image categories:

1. Healthy
2. Pebrine
3. Flacherie
4. Overlap
5. Grasserie

The dataset contains a total of 5,529 images divided into three subsets.

| Dataset Split | Number of Images |
|---|---:|
| Training | 3,868 |
| Validation | 557 |
| Testing | 1,104 |
| **Total** | **5,529** |

The original Train, Validation and Test split was retained during model development.

## 5. Model Architecture

The project uses **MobileNetV2**, a lightweight convolutional neural network (CNN) based on transfer learning.

ImageNet-pretrained weights are used to extract image features.

The architecture consists of:

- MobileNetV2 Base Model
- Global Average Pooling Layer
- Dense Layer with 256 neurons and ReLU activation
- Dropout Layer (0.35)
- Output Dense Layer with 5 neurons and Softmax activation

### Training Approach

**Phase 1: Transfer Learning**

The pretrained MobileNetV2 base layers are frozen, and the classification head is trained.

**Phase 2: Fine-Tuning**

The last 30 layers of MobileNetV2 are unfrozen for fine-tuning, while Batch Normalization layers remain frozen.

The model uses:
- Optimizer: Adam
- Initial Learning Rate: 0.001
- Fine-Tuning Learning Rate: 0.00001
- Loss Function: Categorical Crossentropy
- Evaluation Metric: Accuracy
- Batch Size: 32
- Image Size: 224 × 224

Early Stopping, Model Checkpoint and ReduceLROnPlateau callbacks are used during training.

## 6. Image Preprocessing

The following preprocessing techniques are applied:

- Resizing images to 224 × 224 pixels.
- Converting images into RGB format.
- Normalizing pixel values using MobileNetV2 preprocessing.
- Applying data augmentation to training images.

Data augmentation includes:
- Rotation (15 degrees)
- Width and height shifting (10%)
- Zooming (10%)
- Horizontal flipping

## 7. Model Evaluation

The trained model is evaluated using an independent test dataset containing 1,104 images.

### Overall Performance

| Metric | Result |
|---|---:|
| Test Accuracy | 98.91% |
| Test Loss | 0.0353 |
| Macro F1-Score | 98.90% |
| Weighted F1-Score | 98.92% |

### Class-wise F1-Scores

| Class | F1-Score |
|---|---:|
| Flacherie | 99.50% |
| Healthy | 99.32% |
| Overlap | 99.80% |
| Pebrine | 98.51% |
| Grasserie | 97.38% |

Additional evaluation techniques include:
- Confusion Matrix
- Precision
- Recall
- F1-Score
- Multi-class ROC Curves
- AUC Scores
- Prediction Confidence Distribution

## 8. Model Prediction

The model accepts a silkworm image as input and generates a probability score for each of the five classes.

The class with the highest probability is selected as the predicted category.

A confidence threshold of 60% is used. If the confidence is below this threshold, the system recommends manual inspection.

## 9. Model Export and Deployment

The trained model is saved in the following formats:

- `silkworm_disease_model.keras` – Trained Keras model.
- `silkworm_disease_model.tflite` – TensorFlow Lite model.
- `class_labels.json` – Class label mapping.

The TensorFlow Lite model is intended to support lightweight deployment on edge devices and future hardware integration.

### Model Input Specifications

- Input format: RGB image
- Input dimensions: 224 × 224 × 3
- Preprocessing: MobileNetV2 preprocessing
- Output: Five-class Softmax probability vector

## 10. Future Scope

- Integrate the model with Raspberry Pi or other edge devices.
- Implement real-time disease detection using a camera.
- Integrate disease detection with IoT-based environmental sensors.
- Develop a farmer-friendly web or mobile application.
- Test the model using real-world images under different lighting conditions.
- Explore further model optimization for edge deployment.

## 11. Conclusion

The Silkworm Disease Detection Model demonstrates the application of deep learning and transfer learning in sericulture.

Using MobileNetV2, the system achieved 98.91% test accuracy across five silkworm image categories.

The model provides a foundation for automated disease identification and can be further integrated with IoT-based monitoring solutions under the SeriGuard AI project.

---

**Project Name:** SeriGuard AI  
**Module:** Silkworm Disease Detection  
**Model:** MobileNetV2  
**Domain:** Deep Learning, Computer Vision and Smart Agriculture  
**Programming Language:** Python
