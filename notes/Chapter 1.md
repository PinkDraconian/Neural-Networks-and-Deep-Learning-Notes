---
title: Chapter 1
created: '2020-05-14T16:21:07.954Z'
modified: '2020-05-14T17:10:31.380Z'
---

# Chapter 1
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
