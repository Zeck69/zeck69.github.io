---
layout: home
title: Shine bright like adamon
subtitle: Our datastory
---

# How does actor fame influence movie rating?
- fame in terms of awards, online popularity and connections between actors


## Popularity Analysis
Felix and Marine's part

### Awards Analysis
check

### Rating Icons: Are the big names worth the hype?

To understand the impact of a famous cast, we first need to define what is fame. We will consider the fame of an actor as the % of people that know the actor. Certainly, fame is subjective and context-dependent, and as much we would like to be omnipresent, our analysis will be confined to examining fame within the context of the United States of America. Now that we have our raw data, we need to take a second decision, when is someone famous? In our analysis, we will consider an actor famous only if half the US population knows him/her. Last, we need to estimate the fame of a cast ensemble, for this we will average the fame of the actors by the size of the cast. Once our measures established, we obtain the following 2 metrics per movie, the average fame of a cast, and it's famous to actor ratio (what % of the cast is famous). We find ourselves with a quantitative and a qualitative gauge for fame, now let’s see if all this reach is worth what they say.

#### Fame: evolution over time

As the data we have for fame levels is actual, more recent casts should be more likely to be famous, so one could say that analysing the impact of fame wouldn’t make sense. Yet recent movies have not better ratings than old movies, we can clearly see a downward trend in average ratings over time. Not only that, but average cast fame is fairly stable after 1930’s, which let us conclude that we can interpret the effect of the fame of different casts during different periods similarly.

{% include interactive_fame.html %}

Where does this show up?

{% include genre_distribution.html %}

hallo this workds

{% include interactive_genre_subplots.html %}


## Network Analysis
Part from Emma and Tim

## Financial analysis

The whole time we focussed on ratings as the main metric. But what about money? Is there any link between movie ratings and their financial success? Can we claim that actor fame also influences a movie's revenue potential? Let's have a look!

### Inital Exploration

To start with, we combined the ADA movies dataset (link) with the budget dataset (link) and to get a cleaned dataset where each movie has renvenue and budget data. Afterwards we adjusted them for inflation  with our CPI data (link), to consider the time aspect of the dataset.

Let's first have a look at our data distribution over the years. Which movies surprise you the most when looking at it's rating or revenue?

{% include fin_first_viz.html %}

### Correlation & Regression Analysis
- Pearson correlation is 0.23622, so small positive correlation between higher ratings and higher revenues.
- Let's try to explain relationship of ratings as the independant predictor variable and revenues as the dependant output with linear regression: coef is 7e07, so on average with every additional rating point the movie is making $ 70,000,000 more in revenue.
- The same holds true when adding budget as an independant predictor, proving ratings to be the dominant predictor

{% include fin_lin_reg.html %}

### Quartiles Analysis
- Splitting up the data in rating quartiles (0.25    5.9; 0.50    6.5; 0.75    7.1) and displaying their boxplots also shows trend of movies with higher ratings having higher revenues.
{% include fin_quartiles_box.html %}

### Checking causation
To check for causality and not only correlation between ratings and revenues, we calculated the propensity score for all data points, utilizing budget and year as potential cofounders on the effect of ratings on revenue. We then defined the treshhold for having a high rating the 0.75 quantile. As a result we got the treated group (having a high rating) and the control group (having a not high, i.e. low rating). We then paired matched the datapoints on the propensity score. The consequent average revenues of the treatment group and the control group are XXX and XXX, clearly showing that the group with higher ratings have higher revenues.

- plotted average revenue of treatment and control group and their 95% CI

{% include fin_revenue_paired.html %}

- Conducted T-test to check if difference between treatment and control group is statistically significant. Results show it is.

- Lastly show difference between treatment and control group over years. Treatment group has higher revenues in 88% of the years.

{% include fin_revenue_paired_years.html %}

### Results of financial analysis

- Data shows clear signs that creating a movie that receives good ratings is also highly likely to perform well financially and therefore reward cast and directors


## Conclusion
??? Let's seeeeee
