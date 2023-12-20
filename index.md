---
layout: home
title: How does actor fame influence movie rating? 
subtitle: A datastory by Shine bright like adamon
---

- fame in terms of awards, online popularity and connections between actors




### Awards Analysis
check Marine's part

{% include interactive_genre_subplots.html %}

{% include genre_distribution.html %}

## Popularity Analysis

### Rating Icons: Are the big names worth the hype?
To understand the impact of a famous cast, we first need to define what is fame. We will consider the fame of an actor as the % of people that know the actor. Certainly, fame is subjective and context-dependent, and as much we would like to be omnipresent, our analysis will be confined to examining fame within the context of the United States of America. Now that we have our raw data, we need to take a second decision, when is someone famous? In our analysis, we will consider an actor famous only if half the US population knows him/her. Last, we need to estimate the fame of a cast ensemble, for this we will average the fame of the actors by the size of the cast. Once our measures established, we obtain the following 2 metrics per movie, the average fame of a cast, and it's famous to actor ratio (what % of the cast is famous). We find ourselves with a quantitative and a qualitative gauge for fame, now let’s see if all this reach is worth what they say.

#### Fame: evolution over time

As the data we have for fame levels is actual, more recent casts should be more likely to be famous, so one could say that analysing the impact of fame wouldn’t make sense. Yet recent movies have not better ratings than old movies, we can clearly see a downward trend in average ratings over time. Not only that, but average cast fame is fairly stable after 1930’s, which let us conclude that we can interpret the effect of the fame of different casts during different periods similarly.

{% include historic_fame.html %}

### Initial analysis



From our visual inspection, it looks like the more famous the better the ratings are, but is it worth it? Visually, we might guess that not all levels of fame have a significant increase. As these famous cast are not free, let’s try to find more precisely at what level the difference makes sense. We will try to find which level of fame would give you the best ratings without overspending on famous cast members. In order to do this, we need to assess the impact of fame in the ratings, eliminating any possible cofounders. To isolate the effect of fame on ratings, we have performed a paired matching. In this matching, we compare movies as likely to receive our treatment, which was having a cast known on average by any % of the population. We performed a logistic regression over the size of the cast, their awards, their experience (as in how many movies they have worked on), the number of votes the movie received, the genre, language and country of origin to obtain their propensity score to be a famous cast. With the obtained group of movies to compare the effect of fame, we found no significant difference between the movies with famous and non-famous casts. Have we been lied to? No one likes movies with Brad Pitt or Meryl Streep? Maybe their success is not as consistent as we though…



As you can see, the previous graph contains a slider to choose what threshold is considered for the treatment of the pair matching. Play around with it. Does something stand out to you? The most curious of you, will find out that there is indeed a significant difference for a good part of the levels, just not in the direction you though. As we can see, the difference is significant for low levels of fame, indicating that you should rather have an unknown cast than a medium famous cast. On the other hand, even if we increase our treatment for only very well-known casts (average fame above 75%), the difference is very clear and still not significant. Does this mean that we should throw away our beloved star - packed casts? Not so fast my dear movie visionary, as significance depends on the result of a t-test, low density parts of the movie universe are very hard to conclude on. How many movies are they in which every cast member is known by more ¾ of the population? Not so many, therefore there is a lot of variance and very little significance to the results with this threshold, even if we would like to conclude from our initial assessment that it doesn’t make sense. With our current data, we can only conclude that we are better off with an unknown cast than with a mildly famous cast.

### But beyond the spotlight, would you rather charisma or controversy?

Is all fame good? There are multiple ways to be known, some considered more ethic than others, but does it have an impact? For this analysis, we are going to work with data concerning only the famous actors of a movie, as likeliness or controversy is much more personal and can hardly be generalized over a full cast.



Our initial assessment looks like the cast with extreme values to be best suited. Indeed, a very liked cast will also be very little disliked, but yet we have some unexpected results for casts with a high dislike ratio. There is a balanced choice to make here, and maybe more to untangle than what we see. We will regress a relation between our ratios and our rating, based on the evidence that we have a correlation of value around 0.2 for each ratio with the ratings. After testing multiple models, we realized 3 key facts, errors are highly heteroskedastic, there is strict multicollinearity between our inputs and our parameters are way too big to realistically explain the impact of the ratios, therefore we need to adapt our regression. Once we obtain our model function with restricted features, penalty for large coefficients and heteroskedastic standard errors, we obtain a function with the following representation:

Image of wolfram

As we can see visually, there are clearly 2 points for which our optimization could converge. Stating our constraint as forcing the ratios to sum to 1 and starting our optimization problem at random points, we obtain 2 convergences, either maximizing or minimizing likeliness. This trade off shows that there is no interest in having a neutral cast, and simulating our optimization for 100 times we obtain the following cases:

image

Therefore both cases are viable options.

## Network Analysis
Part from Emma and Tim

## Financial analysis
Our focus is typically on ratings as the primary metric, but isn't the financial aspect of the movie industry just as fascinating? Is there a direct connection between movie ratings and their financial success? And do you think the fame of an actor could sway a movie's revenue potential? Let's dive in and find out!

### Inital Exploration

We started by merging the ADA movies dataset with our budget data, resulting in a curated collection of films where each entry is equipped with both revenue and budget data. These figures were then adjusted for inflation using our CPI data, ensuring that the temporal factors within the dataset are accounted for.

Upon examining the distribution of our data over the years, which movies surprise you the most when looking at their rating or revenue?

{% include fin_first_viz.html %}

### Correlation & Regression Analysis
Diving into the analysis, a Pearson correlation coefficient of 0.23622 indicates a slight positive correlation between higher ratings and increased revenues. Moreover, employing linear regression to model the relationship between ratings (as the independent variable) and revenues (as the dependent variable) yields a coefficient of 7e07. This suggests that, on average, each additional rating point could mean an approximate $70,000,000 increase in movie revenue.

Incorporating the budget as an independent variable confirms that ratings are the dominant predictor, maintaining the established relationship with revenue.

{% include fin_lin_reg.html %}

### Quartiles Analysis
When we segment the data into rating quartiles—specifically, 5.9 (25th percentile), 6.5 (50th percentile), and 7.1 (75th percentile)—the trend persists: movies with higher ratings tend to generate higher revenues.

{% include fin_quartiles_box.html %}

### Checking causation
To distinguish causation from mere correlation between ratings and revenues, we calculated the propensity score for each movie, considering budget and year as potential confounders. We set the threshold for a high rating at the 50th percentile, classifying ratings above 6.5 as 'high'. This categorization yielded two groups for comparison: the treated (high rating) and the control (low rating). After pair matching based on the propensity score, the average revenues of the treatment group and the control group stood at $219,224,169.79 and $106,129,755.70. This underscores that movies with higher ratings typically garner higher revenues.

In the next graphic we visualize the average revenue of both groups, alongside their respective 95% confidence intervals.

{% include fin_revenue_paired.html %}

Afterwards, to see if there is a meaningful difference betwenn the two, a paired T-test is conducted to ascertain the statistical significance of the revenue differences between the treatment and control groups. The results confirm the significance of the disparity. Additionally, when observing the difference between the treatment and control groups over the years, we found that movies in the treatment group outperformed those in the control group revenue-wise in 93% of the years. 

Have a look below to see how treatment and control group revenues change over the years!

{% include fin_revenue_paired_years.html %}

### Results of financial analysis

Finalizing our financial analysis, the data presents compelling evidence that creating a movie with favorable ratings is not only artistically gratifying but is also highly likely to succeed financially, providing great rewards for the cast and directors involved.


## Conclusion
??? Let's seeeeee
