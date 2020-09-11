# Popular Statistics Interview Questions

## 1.How do you assess the statistical significance of an insight?
* Statistical significance tells us if our observation just happened by chance or is a real insight.
* Typically, we use a hypothesis testing:
  * null hypothesis is the opposite of what we want to test
  * choose a statistical test based on data distribution and experiment design
  * check the power of test
  * calculate the statistics and p value
* Common factors to consider on choosing tests:
  * one-sample or two-sample?
  * paired or non-paired?
  * continuous or discrete?
  * mean? variance? proportion?
  * what is the distribution?

## 2. Explain what a long-tailed distribution is and provide examples of relevant phenomena that have long tails. Why are they important in classification and regression problems?
* In long tailed distributions, a high frequency population is followed by a low frequency population, which gradually tails off asymptotically
* Rule of thumb: majority of occurrences (more than half, and when Pareto principles applies, 80%) are accounted for by the first 20% items in the distribution. This happens a lot in business cases.
* Examples:
  * Natural Language
  * Allocation of wealth
* Be careful about the imbalance data in classification problem. Pick the right metrics (F-score, AUC).
* Issue in sampling: maybe try stratified sampling.
* Need to apply monotone transformation like logarithm, sigmoid function...

## 3. What is the Central Limit Theorem? Explain it. Why is it important?
* The CLT states that the arithmetic mean of a sufficiently large number of iterates of independent random variables will be approximately normally distributed regardless of the underlying distribution. i.e: the sampling distribution of the sample mean is normally distributed.
* Used everywhere in hypothesis testing and confidence interval calculation.
* Assumptions: random variables must be iid (independent and identically distributed)

## 4. What is statistical power?
* sensitivity of a binary hypothesis test
* Probability that the test correctly rejects the null hypothesis H0 when the alternative H1 is true. Power = P(reject H0 | H1 is true). As power increases, chances of Type II error (false negative) decrease
* Used in the design of experiments, to calculate the minimum sample size required so that one can reasonably detects an effect. i.e: 'how many times do I need to flip a coin to conclude it is biased?'
* Used to compare tests. Example: between a parametric and a non-parametric test of the same hypothesis

## 5. Explain selection bias (with regard to a dataset, not variable selection). Why is it important? How can data management procedures such as missing data handling make it worse?
* Selection of individuals, groups or data for analysis in such a way that proper randomization is not achieved
* Examples:
  * sampling bias: bias from non-random sample of population
  * cherry picking: specific subset is used to support conclusion
* Why missing data handling make it worse? When the sample is biased, the imputation just creates more biased data.

## 6. Provide a simple example of how an experimental design can help answer a question about behavior. How does experimental data contrast with observational data?
* Experiment design can help us isolate the effect (control the other factors) of treatment.
* Example of difference between experimental and observational data: flu shot reduces the influenza risk based on experimental data; while in reality people get flu shot might have higher infection rate, this is because people have worse health condition would be more likely to take flu shot.

## 7. Is mean imputation of missing data acceptable practice? Why or why not?
* Typically a bad practice
* Potential problems:
  * underestimate the standard deviation
  * distorts correlation between variables toward to zero (recall the formula of correlation, if all values are same with mean, correlation will be 0)    

## 8. What is an outlier? Explain how you might screen for outliers and what would you do if you found them in your dataset. Also, explain what an inlier is and how you might screen for them and what would you do if you found them in your dataset
* Outlier definition:
  * observations that are distant from other observations, usually can happen in long-tailed distribution
  * In normal distribution, 68% of points should be within 1 standard deviation; 95% within 2 standard deviation; 99.7% within 3 standard deviation
* Outlier handling method:
  * depends on the use case; if outlier has a big impact on estimation, we should consider drop it
* Inlier definition:
  * Observation lying within the general distribution of other observed values, e.g. observations recorded in wrong unit (F instead of C)
* Inlier handling method:
  * Inlier is very hard to detect, unsupervised learning might be a way to deal detect it
  * If we are sure about inlier, we should drop them

## 9. How do you handle missing data? What imputation techniques do you recommend?
* If no big harm to power, just simply drop them
* If we do want to impute them, try put those missing records in a separate category (instead of imputing them with a summary statistics and treating them as normal records)
