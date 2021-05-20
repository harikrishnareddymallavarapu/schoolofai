Creating Custom dataset to include random numbers and generate labels which is sum of the random number and the image label
Here we have 2 inputs, the first one is a image matrix and the second input is a random number. The random number in the range of (0,9) is generated using the torch.randint method and its converted to one-hot vector representation

The desired output is to get the image label as one output and the other output is to get the sum of the random number and the image label. Output2 is converted to one-hot representation as we know from the problem that the min and max values would be in the range 0 to 18
