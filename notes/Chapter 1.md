---
attachments: [Clipboard_2020-05-14-18-30-35.png]
title: Chapter 1
created: '2020-05-14T16:21:07.954Z'
modified: '2020-05-14T16:39:09.119Z'
---

# Chapter 1
## Exercises

### Sigmoid neurons simulating perceptrons, part I
> Suppose we take all the weights and biases in a network of perceptrons, and multiply them by a positive constant, `c > 0`. Show that the behaviour of the network doesn't change.

For a perceptron, the following is true:
![](@attachment/Clipboard_2020-05-14-18-30-35.png)
So if we pick a perceptron with one input, a weight of 2 and bias of 4, we will get `2 * x + 4` which can be reformed to `x = -2`
If we then multiply the weights and biases by a positive constant, let's pick `8`, we get `16 * x + 32` which can be reformed to `x = -2`
We notice that as expected, both the results are equal.

### Sigmoid neurons simulating perceptrons, part II
