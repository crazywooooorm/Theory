## Choosing and Characterizing Metrics
* Use funnel to show the structure of the stages of your experiment and define your metrics. The lower stage of the funnel is, the fewer people will be included.

* Difficulties of the metrics come from:
  * Too long to collect the data of that metric
  * Can't have access to the data

* To get more data, we can:
  * User experience research (UER): can go really deep to a small group of people
  * Focus groups: larger participant base and focus on specific group
  * Surveys: contains the biggest participant base but the replies might not be reliable because people don't have to tell the truth and can be easily affected by the design of the survey
  * Check if any external data can help
  * Retrospective analysis to check how metrics work in history.

* To get the confidential intervals of our concerned metric, we can:
  * Calculate the confidence interval based on the distribution (experimental) of the metrics
  * Directly pick the observations based on percentile

* Sensitivity and Robustness: You want to choose a metric that is has high sensitivity, that means the metric can pick up the change you care about. You also want the metric to be robust against changes you don’t care about. It means the metric doesn’t change a lot when nothing you’re interested happened. Sensitivity and Robustness is a trade-off. A/A test is a good way to check robustness.

* A/A test: Tactic of using a testing tool to test two identical variations against each other. In order to make sure your A/A test is correctly set up you should pay attention to 4 main things:
  * Variation: both the control and the variation should be the exact same page. Even if minor differences are present, they might compromise the test results
  * Segmentation: make sure you send the same segment of traffic to both the control and variation. All other things being the same, sending different segments of traffic to your pages can result in a false positive.
  * Goals: track the exact same goals for each page
  * Traffic: it is extremely important to send enough traffic to the experiment. There is no fixed amount that is considered best, but the general consensus in the A/B testing world is a minimum of 10.000 visits and at least 100 goal conversions.


## Designing Experiment
* Unit of diversion: unit of the subject of the experiment. Typical units of diversion includes: User id, Anonymous id (cookie), events, ip address and device id. Each unit has different consistency, we have to decide the unit we use based on the demand of the experiments. If the change will easily be noticed by user (which means user will have extra action based on that change), we should use cookie or user id as our unit as they are more consistent.

* When unit of analysis is same with unit of diversion, the true variability is close to analytical estimate. Image if you focus on click rate, which the unit of analysis should be pageviews. But if we use user id as unit of diversion, those correlated observations (belong to same user) will be put in same test group, which affects the variability.

* Choose the right target for experiment. If the change only affects a small part of people but we take whole population to do the test, the result will be diluted and the change will be hard to have significant result.

* Cohort can subset the population and only focus on those people we care.

* You wouldn't want to put all your traffic on one day, but let the duration cover more time (eg. both weekends and weekdays). On the other way, try small exposure at first to prevent possible risk (some change might cause severe result).

## Analyzing Results
* Sanity checks are necessary for analyzing experiments: Check invariants，Choose some metrics that will not change during during the experiments. Test the invariants, if there are some significant changes than we need to dig deeper on that.

* Simpson's paradox： Rate is higher in one group than another group in each segment, but when aggregate all segments together the result is reversed. In this case it would be better to test in each segments.

* When we have too many variants, it is likely some metrics are just significant by chance. In this case, we can re-run the experiment again and again see if it stay as significant or not, or use some correction methods (Bonferroni correction) to correct the significance level we want.

* Learning effect: When there’s a new change, in the beginning users may against the change or use the change a lot. But overtime, user behavior becomes stable, which is called plateau stage. The key thing to measure learning effect is time, but in reality you don’t have that much luxury of taking that much time to make a decision. Suggestion: run on a smaller group of users, for a longer period of time.

* When drawing conclusions, you have to: first, understand your changes, know the reasons and intuitions behind those changes, and second, check the changes over time (many changes are not actually repeatable because of seasonalities or something else).
