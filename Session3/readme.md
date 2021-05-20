Creating Custom dataset to include random numbers and generate labels which is sum of the random number and the image label
Here we have 2 inputs, the first one is a image matrix and the second input is a random number. The random number in the range of (0,9) is generated using the torch.randint method and its converted to one-hot vector representation

The desired output is to get the image label as one output and the other output is to get the sum of the random number and the image label. Output2 is converted to one-hot representation as we know from the problem that the min and max values would be in the range 0 to 18

## Building the Neural Network Model
The Model takes 2 inputs and generates 2 outputs

Below are the steps on how the network processes the data in different layers

In this design we pass the first input in layer1 and the second input is appended in the layer 3. We could pass in layer 1 but in this design its chosen to pass in layer 3. The convolution layers are generally used for averaging out the impact from neigbourhood pixels which best suits for images so we chose to pass the random number from layer 3 

### Layer 1
1. The first input which is an image of 1x28x28 is passed through a convolution layer with a kernelsize = 5 and out channels as 6. The output of this layer is 6 outputs / features of the size 1x24x24. 
2. The first layer output is passed Relu activation and through Max pooling layer of kernel size 2 and stride 2. Each feature 1x24x24 is max pooled to 1x12x12 size

### Layer 2 
3. The output of the layer 1 is taken as input to second convolution layer which has a kernel size of 5 and out channels as 12. The 6 input tensors of size 1x12x12 is converted to 12 features of size 1x8x8.
4. The output of the second layer convolution operation is passed to a Relu activation and to a max pool layer with kernel 2 and stride 2. Each feature of 1x12x12 is max pooled to size 1x4x4

### Layer 3 
5. The 12 features from output of layer 2 is flattened to [1, 192] tensor and the second input is concatenated to this output. This concatenated tensor acts as input to layer 3
6. The layer 3 takes 1x202 vector as input and generates 120 features as output
7. weighted input of layer 3 neurons are passed through relu activation function

### Layer 4
8. The layer 3 takes 1x120 vector as input and generates 1x60 features as output
9. The weighted input of layer 4 neurons are passed through relu activation function

### Layer 5
10. The layer 4 takes 1x60 vector as input and generates 1x45 features as output
11. The weighted input of layer 5 neurons are passed through relu activation function

### Layer 6 - Output 1
14. The layer 5 takes 1x45 vector as input and generates 1x10 features as output
15. The output of the layer 6 is passed through softmax function to generate the probabilites of the class 

### Layer 7 - Output 2
14. The layer 5 takes 1x45 vector as input and generates 1x19 features as output
15. The output of the layer 7 is passed through softmax function to generate the probabilites of the class 
