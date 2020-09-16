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

## 10. You have data on the durations of calls to a call center. Generate a plan for how you would code and analyze these data. Explain a plausible scenario for what the distribution of these durations might look like. How could you test, even graphically, whether your expectations are borne out?
* Start with exploratory data analysis, check the basic summary statistics of the samples. Then we can use histogram or boxplot to visualize its distribution.
* A possible guess about its duration is lognormal, so log(duration) should be close to a normal distribution, here are some ways to test for normal distribution:
  * QQ plot: if the sample distribution is normal, qq plot would be close to a straight line (same quantile with normal)
  * Kolmogorov Smirnov test: check the largest difference between empirical CDF and target CDF. Kolmogorov Smirnov test can also be used to check other distributions
  * Shapiro-Wilk test: has more power than above, but only works for normal

## 11. Explain likely differences between administrative datasets and datasets gathered from experimental studies. What are likely problems encountered with administrative data? How do experimental methods help alleviate these problems? What problem do they bring?
* Advantages of administrative data:
  * Large coverage of population
  * Captures individuals who may not respond to surveys
  * Regularly updated, allow consistent time-series to be built-up
* Disadvantages of administrative data:
  * Restricted to data collected for administrative purposes
  * Quality issues (missing or error entries) because of lack of researcher control over content
  * Possible data privacy issue

## 12. You are compiling a report for user content uploaded every month and notice a spike in uploads in October. In particular, a spike in picture uploads. What might you think is the cause of this, and how would you test it?
* Horizontally, check if the same phenomenon happened in any specific area, age group, or other demographic groups
* Vertically, check if the same phenomenon happened in Sep or last Oct
* Find a null hypothesis based on your guess, and design tests to check it


## 13. What is root cause analysis? How to identify a cause vs. a correlation? Give examples
* Root cause analysis:
  * Method of problem solving used for identifying the root causes or faults of a problem
  * A factor is considered a root cause if removal of it prevents the final undesirable event from recurring
* Causation Vs Correlation:
  * Causation indicates one variable's change is caused by another variable, while correlation only implies the relation.
  * In experiment design, we can use placebo to check if the treatment does cause the effect.

## 14. What is causal inference and how to do it?
* Causal inference:
  * Causal inference is the process of drawing a conclusion about a causal connection based on the conditions of the occurrence of an effect.
  * Try to estimate the Conditional Average Treatment Effect (CATE) or Individual Treatment Effect (ITE) from experimental or observational data.
* T-learner: Train two models separately for test and control groups, the treatment is estimated by difference between two models. One disadvantage is, the errors of two models will add up
* S-learner: Use single model, treat treatment factor as a normal variable.
* X-learner:
  * X-learner is an extension of T-learner.
  * After we have two models trained separately from test and control groups, we can estimated the difference between test people in control model, and difference between control people in test model
  * sum up the two differences with weight (propensity score), then we get our CATE
* Causal Tree: for a tree based model, change the cost function to maximize 'the treatment effect between test and control groups'

## 15. What is the Law of Large Numbers?
* A theorem that describes the result of performing the same experiment a large number of times. It says that the sample mean, the sample variance and the sample standard deviation converge to what they are trying to estimate

## 16. How do you calculate needed sample size?
* Consider the way to calculate confidence interval. To make sure the sample is within certain interval (confidence interval) of true mean, the sample follows the formula: interval = z * s / sqrt(n), where z is score of normal distribution, s is standard deviation, n is sample size.

## 17. When you sample, what bias are you inflicting?
* Selection bias: An online survey about computer use is likely to attract people more interested in technology than in typical
* Under coverage bias: Sample too few observations from a segment of population
* Survivorship bias: Observations at the end of the study are a non-random set of those present at the beginning of the investigation; only successful companies are included in survey because failed ones don't exist any more

## 18. How do you control for biases?
* Choose a representative sample, preferably by a random method
* Choose an adequate size of sample
* Identify all confounding factors if possible, and include them as additional predictors in statistical analyses

## 19. What are confounding variables?
* Extraneous variable in a statistical model that correlates directly or inversely with both the dependent and the independent variable
* The relationship between an independent variable and a dependent variable is estimated incorrectly if fails to account for the confounding factor

## 20. What are metrics commonly used in classification?
* Recall / Sensitivity / True positive rate:
  * TP/(TP + FN)
  * High when FN (type 2 error) is low
* Precision / Positive predictive value:
  * TP/(TP + FP)
  * High when FP (type 1 error) is low
* Specificity / True negative rate:
  * TN/(TN + FP)
  * High when FP (type 1 error) is low
* Accuracy:
  * (TP + TN)/(TP + TN + FP + FN)
  * High when FP and FN are low
* ROC / AUC:
  * ROC plot depicts sensitivity Vs FP rate (FP/(FP + TN)).
  * AUC is the area under ROC curve.
  * The perfect classifier should have AUC = 1, which means sensitivity is always 100% and FP rate is always 0.
  * AUC is not sensitive to unbalanced data
* F1-Score:
  * 2*(precision*recall)/(precision+recall) = TP/(TP + 0.5*(FP + FN))
  * Accuracy cares more about TP and TN, while if FN and FP is more important (e.g., in diagnosis of cancer, we need to minimize FN), F1-Score is a better metric to use. F1-Score is more used in unbalance data.

## 21. Poisson distribution
* Expresses the probability of a given number of events occurring in a fixed interval of time. For example, the number of patients arriving in an emergency room between 10 and 11 pm
* Only one parameter in its pdf, which equals to its mean and variance
* Poisson process is a memoryless stochastic point process; that an event has just occurred or that an event hasn't occurred in a long time give us no clue about the likelihood that another event will occur soon.

## 22. You are running for office and your pollster polled hundred people. 56 of them claimed they will vote for you. Can you relax?
* The distribution of how many people vote for you (x) is a binomial distribution, with E(X) = np, Var(x) = np(1-p)
* If we focus on p, then E(p) = E(x/n) = p, variance = Var(x/n) = Var(x)/n^2 = p(1-p)/n
* When n is big enough, the mean approximates to normal distribution
* Confidence interval is p +- z * sqrt(p(1-p)/n). If null hypothesis is p = 0.5, then we can calculated the 95% confidence interval for p is [0.402, 0.598]. 0.56 is still not enough to draw a conclusion.
