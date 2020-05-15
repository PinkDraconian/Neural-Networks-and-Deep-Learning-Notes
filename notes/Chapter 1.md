---
attachments: [Clipboard_2020-05-15-10-57-37.png]
title: Chapter 1
created: '2020-05-14T16:21:07.954Z'
modified: '2020-05-15T09:09:23.812Z'
---

# Chapter 1
## Summary

### Perceptrons
For a perceptron, the following is true about the output:
$0$ if $w\cdot x + b \leq 0$
$1$ if $w\cdot x + b > 0$

### Sigmoids
$\sigma(z) \equiv \frac{1}{1+e^{-z}}$ where $z = w\cdot x + b$




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

























