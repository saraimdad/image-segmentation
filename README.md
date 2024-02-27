# image-segmentation

## Project Overview
This project aims to implement image segmentation, specifically semantic segmentation, using UNetV2 architecture for applications in self-driving cars. Semantic segmentation is a critical task in autonomous vehicles, as it involves the pixel-wise classification of objects in an image, enabling the vehicle to understand and interpret its surroundings. UNetV2, an improved version of the original UNet, is utilized for its effectiveness in capturing intricate details and preserving spatial information during the segmentation process.

## Dataset
The dataset originates from the Coursera Deep Learning Specialization course and is curated to encompass a variety of road scenarios, lighting conditions, and diverse objects encountered in real-world driving situations. It contains both masked and unmasked images. The masked images have pixel-level annotations, highlighting the segmented areas of interest such as roads, vehicles, pedestrians, etc., while the unmasked images serve as the input to the segmentation model without pixel-level annotations.

## Data Preprocessing
The data preprocessing pipeline involves reading image and mask files, converting pixel values to floating-point format, and simplifying masks to a single channel. The images are then resized to a uniform 96x128 pixels, preparing them for training the UNetV2 model. The entire dataset is processed, yielding a processed_image_ds ready for semantic segmentation model training.

## Model 
The UNetV2 architecture is composed of encoder and decoder blocks, implemented in TensorFlow. The encoder block downsamples input tensors through two convolutional layers with ReLU activation, optionally incorporating dropout and max pooling. On the other hand, the decoder block performs upsampling using transposed convolution and merges expansive and contractive inputs before applying two convolutional layers. 
These blocks collectively construct the UNetV2 model, providing a powerful tool for pixel-wise semantic segmentation. The model takes input tensors of size 96x128x3 and outputs segmentation maps with dimensions corresponding to the specified number of output classes. The model is compiled using the Adam optimizer and categorical cross-entropy loss, which is suitable for multi-class segmentation tasks. The He normal initializer is used for convolutional layer kernel initialization, promoting stable and efficient training. The model was trained for 40 epochs with a batch size of 32. The final model effectively captures intricate details and spatial information, making it well-suited for self-driving car applications. 

## Evaluation 
The model was evaluated using the test set and had the following accuracy graph:
<p align="center" width="100%"><img width="556" src="https://github.com/saraimdad/image-segmentation/assets/157117492/18ab13c9-0bbf-4fef-ab45-b0a37f27cf2c"></p>

## Acknowledgements
https://www.coursera.org/learn/convolutional-neural-networks
https://www.deeplearning.ai/program/deep-learning-specialization/
