# Popular Statistics Interview questions

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
