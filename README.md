# XOR-MNIST-Neural-Networks-from-Scratch
XOR & MNIST Classification Neural Networks from Scratch

Executive Summary
This report covers two neural network projects implemented from scratch:
1. XOR Problem (Binary Classification)
○ Architecture: 2 → 4 → 1
○ Accuracy: 100%
2. MNIST Digit Classification (Multi-class)
○ Architecture: 784 → 128 → 64 → 10
○ Test Accuracy: 98.25% (Target: >90%)
○ Mini-batch Size: 25, Epochs: 20

Core Architecture Functions(Reused in Both Projects)
1. initialize_parameters_deep() - Initialize weight matrices (W) and bias vectors (b) for all
layers
2. linear_forward(): Compute linear transformation: Z = W·A + b
3. linear_activation_forward()-Combine linear transformation with activation function
4. compute_cost(AL, Y) Calculate loss for current predictions
5. linear_backward(dZ, cache)- Compute gradients for weights and biases
6. sigmoid_backward(dA, cache)-Backprop through sigmoid activation
7. relu_backward(dA, cache)- Backprop through ReLU activation
8 . linear_activation_backward()-Combine activation and linear backprop
9.update_parameters(params, grads, learning_rate)- Perform gradient descent update

Project-Specific Details
XOR Project
● Architecture: 2 → 4 → 1
Activation: Sigmoid (hidden and output)
● Loss: Binary Cross-Entropy
● Data: 4 fixed samples
● Training: 5000 iterations
● Optimization: Full-batch gradient descent
● Accuracy - 100%

MNIST Project
● Architecture: 784 → 128 → 64 → 10
● Activation: ReLU (hidden), Softmax (output)
● Loss: Categorical Cross-Entropy
● Training Data: 60,000 samples; Test Data - 10,000 samples
● Training: 20 epochs
● Batch size: 25
● Learning Rate - 0.1
● Optimization: Mini-batch gradient descent
● Accuracy - 98.25%


Empirical Results & Parameter Tweaking
Number of training examples 30000-
Epoch 1/20, Cost: 0.7030
Epoch 20/20, Cost: 0.0008
Accuracy -98.25%
Number of training examples 60000-
Epoch 1/20, Cost: 0.7030
Epoch 20/20, Cost: 0.0008
Accuracy - 98.25%
Observation - Even though the Cost is equal in both cases, the accuracy is more when
the number of training examples in 60000
This can be explained by the fact that cost function is a smooth, differentiable surface that
guides the optimizer. Accuracy is a non-differentiable 'final score.' A model can become
more confident (lower cost) without actually getting more images correct, or it can rearrange its errors
such that the average loss remains stable while the number of correct hits fluctuates.


I have used 60000 training examples for all the experiments below:
Baseline:
Learning Rate - 0.1
Batch Size - 25
Hidden Layers - [128, 64]
Test Accuracy - 98.25%

Exp -1
Learning Rate - 0.75
Batch Size - 25
Hidden Layers - [128, 64]
Test Accuracy - 9.80%
Reason - Learning rate too high (0.75) caused instability and overshooting during
optimization, preventing convergence to optimal weights

Exp -2
Learning Rate - 0.01
Batch Size - 25
Hidden Layers - [128, 64]
Test Accuracy: 96.87%
Reason - Learning rate too low (0.01) resulted in slower convergence and the model getting
stuck in suboptimal local minima.

Exp -3
Learning Rate - 0.1
Batch Size - 128
Hidden Layers - [128, 64]
Test Accuracy: 97.51%
Reason - Larger batch size (128) reduced gradient noise but led to poorer generalization

Exp -4
Learning Rate - 0.1
Batch Size - 25
Hidden Layers - [256, 128]
Test Accuracy - 98.37%
Reason - Increased network depth (adding more hidden layers) improved model capacity to
learn complex patterns, achieving slightly better accuracy.