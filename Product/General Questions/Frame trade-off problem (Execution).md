# How do you decide between displaying Facebook’s ‘People You May Know (PYMK)’ feature or an Advertisement?

[Origin post](https://stellarpeers.com/decide-between-facebooks-people-you-may-know-feature-or-advertisement/)

## Find product goal of each feature, and their common metric
* Find north star metric for each feature
  * For PYMK, product goal is to make users expand their network and make them more adherent to the platform. North star would be time spent engaging with new friends from PYMK.
  * For 'advertisement', product goal is to make users find and consume more. North star would be number of views/clicks per ad.
* Find common metric and transform feature metrics to it
  * Essentially, we care about **total ad revenue**, which is the common metric.
  * For PYMK, time spent can be translated to impressions during that time, then translated to ad revenue
  * For 'advertisement', number of views/clicks can be easily translated to total ad revenue during a period of time.

## Define segments
* Feature might have different effects on different user segments.
* PYMK will work better on new users as they don't have many friends yet.
* Advertisement will work better on existing users as we have enough profile info to recommend ads.
* If we don't test by segments, these effects might be averaged

## Exp design
* For user segment, we define three segments based on time since registration and number of friends:
  * new user with few friends
  * semi-user with more friends
  * existing user with more friends
* For test groups, we set three groups:
  * no PYMK no advertisement (holdout)
  * PYMK
  * advertisement
* Metric: total ad revenue during a certain time
