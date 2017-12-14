---
layout: default
---

This article is a brief translation of the blog post [Nine levels of EM algorithm](http://mp.weixin.qq.com/s/NbM4sY93kaG5qshzgZzZIQ) by Chunqi Shi. 
In addition, I add some personal explaination and comprehension. 

It aims at providing an introduction to EM algorithm. In specific, Shi divides his understanding of EM algorithm into 9 levels. 

_(If you have any question or doubt about this article, pls contact me @ hanggao1@umbc.edu)_


# [](#header-1) 9 Levels of EM Algorithm Comprehension 
1. EM is E + M
2. EM is a way to construct local lower bound
3. K-means is a Hard EM algorithm
4. From EM to general EM
5. VBEM is a special case of general EM
6. WS algorithm is another special case of general EM
7. Gibbs Sampling is also a special case of general EM
8. WS algorithm is a brief version of VAE and GAN combination
9. The unity of KL divergence

## [](#header-2) EM algorithm is E expectation + M maximization

\(Do. & Batzoglou\) gives a classic example about EM algorithm in [What is the expectation maximization algorithm?](https://www.nature.com/articles/nbt1406#f1)
Consider a simple coin flipping experiment in which we are given a pair of coin A and B of unknown biases, \\(\theta_A\\) and \\(\theta_B\\) respectively. 

