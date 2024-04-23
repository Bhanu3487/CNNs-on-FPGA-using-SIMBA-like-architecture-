# CNNs-on-FPGA-using-SIMBA-like-architecture-
Certainly! Here's the formatted version for your README.md file:

---

## Project Overview

In this project, we implemented convolutional neural networks (CNN) on an FPGA using a SIMBA-like architecture.

### Dataset and Model

We utilized the MNIST handwritten digits dataset and a pre-trained model containing trained convolutional weights and biases, as well as weights and biases of fully connected layers 1 and 2. Utilizing a pre-trained model helps optimize prediction without the need for extensive training, which can be resource-intensive.

### Prediction Process

1. **Convolution Operation**: We loaded the convolution weights and biases onto the FPGA through a .coe file and performed convolution on the input image (28x28 pixels). This function is done on the fpga. The rest is done in python.

   The Simba architechture is implemented in the following heirarchical order from top to bottom: 
  a) The top module collects all the pixels from 28x28 image and passes it to the global_pe module  
  b) The global_pe calls four processing elements  
  c) Each processing elements implements 8 vector mac units parallely  
  d) Further each vector mac unit implements 9 multipliers parallely  

2. **Image Processing**: The output of the convolution operation was received in the form of characters, which were converted to float values. We then passed these values through subsequent functions.

3. **Activation Function (ReLU)**: After convolution, we applied the ReLU activation function to introduce non-linearity into the model.

4. **Max Pooling**: Downsampled feature maps obtained from convolutional layers using max pooling, reducing dimensionality while preserving important features.

5. **Fully Connected Layers**: Output from convolutional and pooling layers was passed through fully connected layers, integrating spatial information and performing classification based on learned features.

6. **Output Conversion**: Finally, the output of fully connected layers, typically logits, was converted into a human-readable format, such as characters representing digits in the case of MNIST.

---
