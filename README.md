# FalconEye: Off-Road Semantic Scene Segmentation
Achieved Validation mIoU: 0.6340
This project was developed for the Off-Road Semantic Scene Segmentation Challenge. It utilizes a Deep Learning approach to identify 10 distinct terrain classes in unstructured desert environments, providing a critical foundation for autonomous off-road navigation.
# Project Overview
Navigating off-road terrain is a major challenge for AI because it lacks the structured cues (like lane markings) found in urban environments. FalconEye uses a robust U-Net architecture to classify every pixel in an image, ensuring safe path planning for autonomous rovers.
  Key Performance
Final Validation mIoU: 0.6340
Target Classes: 10 (Trees, Rocks, Sky, Sand, Logs, etc.)
Backbone: ResNet34 (Pre-trained on ImageNet)
# Technical Architecture
Framework: PyTorch
Model: U-Net (Encoder-Decoder Architecture)
Encoder: ResNet34 (Leveraging Transfer Learning)
Loss Function: Cross-Entropy Loss (Pixel-wise)
Optimizer: Adam with a learning rate of 1*10^-6
# Challenges & Solutions
The "Mask Mapping" BreakthroughThe primary technical challenge was a mismatch between the visual representation of the masks (pixel values 100, 200, 255) and the required class IDs (0–9).
Solution: I engineered a custom data-loading pipeline that remapped these high-range values into discrete integers. This fix allowed the model to begin learning successfully, moving the mIoU from near-zero to over 60%.
# How to RunEnvironment: Open the .ipynb file in Google Colab.
Dataset: Ensure the Offroad_Segmentation_Dataset is uploaded to your environment or Google Drive.
Setup: Run the first cell to install segmentation-models-pytorch.
Inference: To use the trained weights, load best_model.pth using torch.load().
Python
# Quick Load Example
import torch
model.load_state_dict(torch.load('best_model.pth'))
model.eval()
# Results Visualization
The model shows high precision in identifying large obstacles like Rocks and Trees, while maintaining a clean boundary for the Sky.[Image showing comparison of original image, ground truth mask, and model prediction]
# Saanvi Guglani - Student B Tech AI and ML
Note for the Judges
The model was trained for 40 epochs on a T4 GPU. Further improvements can be made by implementing Weighted Cross-Entropy to handle rare classes like "Flowers" or "Logs" more effectively.
# Payload-SaanviGuglani
