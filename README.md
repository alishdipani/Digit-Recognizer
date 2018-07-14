# MNIST-Classifier

### [MNIST Dataset](http://yann.lecun.com/exdb/mnist/)

MNIST dataset has 28x28 grayscale images of digits 0-9. The dataset has 60000 training images and 10000 testing images.

![alt text](DataVisualization.png)

### Implementation

## 1. Pytorch

[IPython Notebook](MNIST_Classifier_PyTorch.ipynb) <p>
Model : Input(28x28x1) -> Conv1(28x28x4) -> ReLU(28x28x4) -> Conv2(28x28x8) -> ReLU(28x28x8) -> Max_Pool1(14x14x8) -> Conv3(14x14x16) -> ReLU(14x14x16) -> Conv4(14x14x32) -> ReLU(14x14x32) -> Max_Pool2(7x7x32) -> Fully_Connected_Layer1(1000) -> ReLU(1000) -> Fully_Connected_Layer2(10) <p>
Kernel size: 5 <p>
Padding : 2 <p>
Stride : 1 <p>
Pool size : 2 <p>
Pool Stride : 2 <p>
Batch Size : 128 <p>
GPU use: No <p>
Iterations : 4300 <p>
Test set Accuracy : 98.12% <p>

## 2. Tensorflow

# 2.a. Standard CNNs

[IPython Notebook](MNIST_Classifier_Tensorflow.ipynb) <p>
Model: Input(28x28x1) -> Conv1(28x28x4) -> ReLU(28x28x32) -> Max_Pool1(14x14x32) -> Conv2(14x14x64) -> ReLU(14x14x64) -> Max_Pool2(7x7x64) -> Fully_Connected_Layer1(1024) -> ReLU(1024) -> Dropout(1024) -> Fully_Connected_Layer2(10)
Kernel size: 5 <p>
Padding : 2 <p>
Stride : 1 <p>
Pool size : 2 <p>
Pool Stride : 2 <p>
Dropout Rate : 0.4 <p>
Batch Size : 128 <p>
GPU used : No <p>
Iterations : 4300 <p>
Global Steps/sec : 2 <p>
Test set Accuracy : 97.99% <p>

# 2.b. Depthwise Separable CNNs

-Inspired from [MobileNet](https://arxiv.org/abs/1704.04861) <p>
[Summary Of MobileNet and Depthwise Convolutions](MobileNet_Summary.pdf) <p>
-Used Depthwise Sepereable Convolutions instead of Standard Convolutions <p>
-Model is 3 times faster (Global steps/sec = 6 and time/100 steps = 20 sec) <p>
-A slight accuracy drop of 1.5% <p>

[IPython Notebook](MNIST_Classifier_MobileNet_Tensorflow.ipynb) <p>
Model: Input(28x28x1) -> Depthwise_Separable_Conv1(28x28x4) -> ReLU(28x28x32) -> Max_Pool1(14x14x32) -> Depthwise_Separable_Conv2(14x14x64) -> ReLU(14x14x64) -> Max_Pool2(7x7x64) -> Fully_Connected_Layer1(1024) -> ReLU(1024) -> Dropout(1024) -> Fully_Connected_Layer2(10) <p>
Kernel size: 5 <p>
Padding : 2 <p>
Stride : 1 <p>
Pool size : 2 <p>
Pool Stride : 2 <p>
Dropout Rate : 0.4 <p>
Width Multiplier : 1 <p>
Resolution Multiplier : 1 <p>
Batch Size : 128 <p>
GPU used : No <p>
Iterations : 4300 <p>
Global Steps/sec : 6 <p>
Accuracy : 96.5% <p>
  
![alt text](DataVisualization_Prediction.png)
