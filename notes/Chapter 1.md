---
attachments: [Clipboard_2020-05-15-10-57-37.png]
title: Chapter 1
created: '2020-05-14T16:21:07.954Z'
modified: '2020-05-16T08:15:49.580Z'
---

# Chapter 1
## Summary

### Perceptrons
For a perceptron, the following is true about the output:
$0$ if $w\cdot x + b \leq 0$
$1$ if $w\cdot x + b > 0$

### Sigmoids
$\sigma(z) \equiv \frac{1}{1+e^{-z}}$ where $z = w\cdot x + b$

### Cost / Loss function
$C$ is the quadratic cost function or mean squared error (MSE) function
$C(w,b) \equiv \frac{1}{2n} \sum_x \| y(x) - a\|^2$
- $w$ is the collection of all weights in the model
- $b$ is the collection of all biases in the model
- $n$ is the total number of training samples
- $a$ is the vector of outputs from the network when $x$ is an input
- $x$ are all the training inputs
- $\|v\|$ denotes the length of the vector $v$

Why a loss function? We want to find a way to minimize the error in our network that also changes with small changes in our weights and biases.

### Gradient descent vector
$\Delta C \approx \nabla C \cdot \Delta v$ where $\nabla C \equiv \left(\frac{\partial C}{\partial v_1}, \ldots, \frac{\partial C}{\partial v_m}\right)^T$
$w_k \rightarrow w_k' = w_k-\eta \frac{\partial C}{\partial w_k}$
$b_l \rightarrow b_l' = b_l-\eta \frac{\partial C}{\partial b_l}$

Issue? Since the cost function requires us to calculate every training input and take the average. This means that for large training sets, learning can be very slow.
Solution? Stochastic gradient descent, taking a random sample of input to calculate the cost.

## Exercises

### Sigmoid neurons simulating perceptrons, part I
> Suppose we take all the weights and biases in a network of perceptrons, and multiply them by a positive constant, $c > 0$. Show that the behaviour of the network doesn't change.

For a perceptron, the following is true about the output:
$0$ if $w\cdot x + b \leq 0$
$1$ if $w\cdot x + b > 0$

So if we pick a perceptron with one input, a weight of 2 and bias of 4, we will get $2 * x + 4$ which can be reformed to $x = -2$
If we then multiply the weights and biases by a positive constant, let's pick $8$, we get $16 * x + 32$ which can be reformed to $x = -2$
We notice that as expected, both the results are equal.

### Sigmoid neurons simulating perceptrons, part II
> Suppose we have the same setup as the last problem - a network of perceptrons. Suppose also that the overall input to the network of perceptrons has been chosen. We won't need the actual input value, we just need the input to have been fixed. Suppose the weights and biases are such that $w⋅x+b≠0$ for the input $x$ to any particular perceptron in the network. Now replace all the perceptrons in the network by sigmoid neurons, and multiply the weights and biases by a positive constant $c>0$. Show that in the limit as $c→∞$ the behaviour of this network of sigmoid neurons is exactly the same as the network of perceptrons. How can this fail when $w⋅x+b=0$ for one of the perceptrons? 

Suppose the same one-perceptron network as used in the last exercise ($2 * x + 4$) and choose $x = 1$. Then our perceptron output will be $1$
If we make that a sigmoid following the formula (with $z = 6$): $\sigma(z) \equiv \frac{1}{1+e^{-z}}$, we get $0.9975$

If we multiply our weights and biases by $10^{1000}$:
- Perceptron: $1$ (Rule shown in previous question)
- Sigmoid: $\frac{1}{1\:+\:e^{-\left(20^{1000}\:+\:40^{1000}\right)}} = 1$

However, when $w⋅x+b=0$, then our sigmoid function will return $0.5$, which will remain the case even after multiplying all weights and biases.

### A simple network to classify handwritten digits
> There is a way of determining the bitwise representation of a digit by adding an extra layer to the three-layer network above. The extra layer converts the output from the previous layer into a binary representation, as illustrated in the figure below. Find a set of weights and biases for the new output layer. Assume that the first 3 layers of neurons are such that the correct output in the third layer (i.e., the old output layer) has activation at least 0.99, and incorrect outputs have activation less than 0.01. ![](@attachment/Clipboard_2020-05-15-10-57-37.png)

First, we map the digits to their binary representation
$0 = 0000$, $1 = 0001$, $2 = 0010$, $3 = 0011$, $4 = 0100$, $5 = 0101$, $6 = 0110$, $7 = 0111$, $8 = 1000$, $9 = 1001$

We see that the first output neuron should only fire when the answer is 8 or 9, therefor, if we set all the weights to $0$ but $w_{8} = 1$ and $w_{9} = 1$, we can then set $b = 0$.
That process can be repeated for the 3 other output neurons.

### Learning with gradient descent, part I
> Prove the assertion of the last paragraph. Hint: If you're not already familiar with the [Cauchy-Schwarz inequality](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Schwarz_inequality), you may find it helpful to familiarize yourself with it.

Wasn't able to successfully solve. I found this section to be very hard to envision mathematically.

### Learning with gradient descent, part II
> I explained gradient descent when C is a function of two variables, and when it's a function of more than two variables. What happens when C is a function of just one variable? Can you provide a geometric interpretation of what gradient descent is doing in the one-dimensional case?

With just one variable, we have to find the minimum of line which can be done by derivation.

### Learning with gradient descent, part III
> An extreme version of gradient descent is to use a mini-batch size of just $1$. That is, given a training input, $x$, we update our weights and biases according to the rules $wk→w′k=wk−η∂Cx/∂wk and bl→b′l=bl−η∂Cx/∂bl$. Then we choose another training input, and update the weights and biases again. And so on, repeatedly. This procedure is known as online, on-line, or incremental learning. In online learning, a neural network learns from just one training input at a time (just as human beings do). Name one advantage and one disadvantage of online learning, compared to stochastic gradient descent with a mini-batch size of, say, $20$.

Advantage: It's 20 times faster than a stochastic gradient descent with a mini-batch size of $20$
Disadvantage: The cost function could be very far away from the actual cost function across the whole training set.



















