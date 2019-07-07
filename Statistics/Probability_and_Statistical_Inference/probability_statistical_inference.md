# Probability & Statistical Inference

## Introduction to Probability
* Sets and sample spaces
* Counting methods: permutation and combination
* Conditional probabilities: law of total probability, Bayes' formula

## Random Variables
* Discrete random variables and continuous random variables, jointly distributed random variables
* probability density functions (PDF) and cumulative density functions (CDF)  
* Distribution of a function of a random variable

## Expectation and Variance
* Properties of expectation and variance for discrete and continuous random variables
* Moment generating functions
* Covariance and correlation

## Distributions
### Discrete
* Bernoulli distribution -> Binomial distribution -> Multinomial distribution
* Poisson distribution: approximation to binomial distribution when n is large but p is small
* Geometric distribution: number of failures before first success
* Negative binomial distribution: number of failures before r-th success
* Hypergeometric distribution: distribution of the sample without replacement. It becomes binomial distribution if replacement is allowed in sampling.

### Continuous
* Uniform distribution
* Exponential distribution: usually used to describe the lifetime or time between unlikely events, e.g. decay of the atom. Exponential distribution is the only memoryless distribution of continuous distributions （Geometric distribution is the only memoryless distribution of discrete distributions）, which means P(X>s+t|X>s)=P(X>t). Basically, memoryless property means if a machine's status doesn't change (which means, regardless of the depreciation, λ is same), the probability of it can run for t hours is same with the probability it can run (s+t) hours after it has already run for s hours.
* Gamma distribution: distribution of the sum of several (α) Exponential distributions.
* Beta distribution: very popular in bayesian statistics because of its great conjugate property. 
* Normal distribution -> Bivariate normal distribution -> Multivariate normal distribution  
