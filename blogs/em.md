---
layout: default
---

This article is a brief translation of the blog post [Nine levels of EM algorithm](http://mp.weixin.qq.com/s/NbM4sY93kaG5qshzgZzZIQ) by Chunqi Shi. 
In addition, I add some personal explaination and comprehension, along with sections of relevant papers. 

It aims at providing an introduction to EM algorithm. In specific, Shi divides his understanding of EM algorithm into 9 \"levels\". 

_(If you have any question or doubt about this article, pls contact me @ hanggao1@umbc.edu)_


# [](#header-1) 9 ways of EM Algorithm Comprehension 
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

Consider a simple coin flipping experiment in which we are given a pair of coin A and B of unknown biases, \\( \theta_A \\) and \\( \theta_B \\) respectively \(i.e., 
given any flip, coin A will land on heads with probability \\(\theta_A\\) and tails with probability \\( 1-\theta_A \\) and similar for coin B\). 

If the goal is set to estimate \\(\Theta = \(\theta_A, \theta_B\)\\), we can divide the experiment into n repeated runs of the following procedure: (1) randomly choose one of the two coins;
(2) and perform m independent coin tosses with the selected coin. 

In other words, we keep track of two vectors \\( x = \(x_1, x_2, ..., x_n\) \\) and \\( z = \(z_1, z_2, ..., z_n\) \\),
where \\( x_i \in \\{0, 1, 2, ..., m\\} \\) is the number of heads observed during the ith set of tosses, and \\( z_i \in \\{A, B\\} \\)
is the identity of the coin used for ith set of tosses.  

In this setting, parameter estimation is known as the complete data case (values of all relevant variables are known), then \\( \theta_A \\) and \\( \theta_B \\)
can be given as, \\( \hat{\theta_A} = \frac{H_A}{H_A + T_A} \\) and \\( \hat{\theta_B} = \frac{H_B}{H_B + T_B} \\), where  \\( H_A \\) is the # of heads using coin A and \\( T_A \\) is the # of tails using coin A and similiar for B. 

<figure>
  <img src="{{site.url}}/assets/images/em/image_1.gif" alt="Parameter estimation for complete and incomplete data"/>
  <figcaption>Fig 1: Parameter estimation for complete and incomplete data</figcaption>
</figure>

The above estimation is known as maximum likelihood estimation in statistical literature, i.e., it gives a solution of the parameters \\( \hat{\Theta} = \(\hat{\theta_A}, \hat{\theta_B}\) \\) that
maximize the logarithm of joint probability (or log-likelihood) \\( logP\(x, z; \Theta\) \\).

However, when it comes to incomplete data case, for example, we are only given recorded head counts \\( x \\), without the identities \\( z \\) of the coin used for each set of tosses. 

### [](#header-3) CITATIONS:
* Fig 1: \(Do. & Batzoglou\) [What is the expectation maximization algorithm?](https://www.nature.com/articles/nbt1406#f1)