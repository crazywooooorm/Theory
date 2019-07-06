# Analysis of Variance and Design of Experiments
Notes based on [Penn State STAT 502](https://newonlinecourses.science.psu.edu/stat502/node/1/)

## ANOVA Foundation
* Why do we use ANOVA? We want to know if the treatments have significant affects on our targets, while when we have more than two groups, the alpha (probability of type I error) of traditional one-pair test gets inflated (true_alpha = 1 - (1-alpha)^(number of comparisons)), to test the total null hypothesis (mean1 = mean2 = ... = meanN), we need to use ANOVA (F test).
* How ANOVA works? Calculate the total_variance (observation - total_mean) and treatment_variance (treatment_mean - total_mean), then get the error_variance (total_variance - treatment_variance). Divided by degree of freedom to get Mean Squares of treatments and error. F statistics = MS_treatment/MS_error.
* What to do when we reject the null hypothesis of ANOVA? Typically we use these methods to figure out which groups have significant differences:
  * Tukey procedure
  * Fisher’s Protected Least Significant Difference (LSD)
  * Bonferroni and Scheffe methods
  * Dunnett’s mean comparison method

## ANOVA Model
* Effects Model: Y_ij = μ + τ_i + ϵ_ij, where μ is the grand mean, τ_i is the deviation due to treatment and ϵ_ij is the error term. Under null hypothesis, τ_i would be 0.
* Assumptions for residuals (ϵ_ij):
  * normally distributed
  * mean of 0
  * independent
  * equal variance among treatment levels (homogeneity)
* If the assumptions of residuals are not met, transformations (logarithmic, quadratic) can be applied to Y.
* Besides all the diagnosis on assumptions, we still need to do a power analysis for the model.

## Multi-Factor ANOVA
* Suppose we have two factors a and b, the effects model will become Y_ijk = μ + a_i + b_j + ab_ij + ϵ_ijk. The effect of factors and their interactions can be saw observed in the [graph of lines of means](https://newonlinecourses.science.psu.edu/stat502/node/153/).
* For Multi-Factor models, there are two situations:
      * Crossed: each level of treatments occur with all levels of other treatments (factorial). Null hypothesis only focuses on the marginal means of different factors.
      * Nested: levels of a treatment are unique to different levels of other treatments. Null hypothesis focuses on the means of the crossed subgroups of factors.
  
