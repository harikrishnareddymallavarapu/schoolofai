<b>1. What is a neural network neuron?</b>
Neuron is a fundamental unit in a neural network model. It is nothing but a set of inputs, set of weights and an activation function. It does a weighted opertaion on the inputs it receives and applies an activation fucntion to generate a linear or non-linear output. Neural networks are collection of neurons connected in layers and each neuron generally captures characteristics and patterns of the inputs which is difficult to do in a normal fetaure engineering process.

2. What is the use of the learning rate?
The learning rate is a hyperparameter that controls how much to change the model in response to the estimated error each time the model weights are updated. If the learning rate is too small then it may result in long training process and if its too large then it may result in unstable training process and might never converge.

3. How are weights initialized?

1. All the weights should not be initialized with the same value as all the weights get same update during the training and they would all remain with a same value.
2. If the weights are initialized to small values with tanh or sigmoid activation function then it might result in zero gradients at some point of time in the training and might result result in no updation of weights (Vanishing Gradients problem)
3. If the weights are initialized to large values awith tanh or sigmoid activation function then it might result in saturation of neurons meaning no gradients 
4. Initialization techniques like HE initialization or Xavier initialization can be used which multiply the random initializations by a scaling factor to ensure that the weights are neither too much bogger than 1 or too much smaller than 1

4. What is "loss" in a neural network?
The loss is the error that has been made by the neural network model. Its the penalty that will be imposed to the model for generation of error and this will be used for updation of the weights using gradients and back propogation. Depending on the nature of the problem we have various loss functions like Mean Squared Erorr (MSE), Binary Cross Entropy (BCE), Cross Entropy, Sparse Category Cross Entropy, KL Divergence

5. What is the "chain rule" in gradient flow?
The chain rule of differentiation leads to Gradient flow rule. 	
The chain rule is a formula to compute the derivative of a composite function. For example if variable z depends on y which itself depends on variable x then z is also dependent on x via the intermediate variable.
In this case the chain rule states that
dz/dx = dz/dy * dy/dx

In deep learning the input of a any layer is dependent on its previous layer (except input layer) which leads to a composite function at the output. The gradient calculated at the end is traversed back to the hidden layers using the chain rule principle to update the weights there by enabling the training of the network.  
