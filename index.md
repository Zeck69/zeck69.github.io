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


## Financial Analysis
The whole time we focussed on ratings as the main metric. But what about money? Is there any link between movie ratings and their financial success? Can we claim that actor fame also influences a movie's revenue potential? Let's have a look!

### Inital Exploration

To start with, we combined the ADA movies dataset (link) with the budget dataset and to get a cleaned dataset where each movie has renvenue and budget data.

{% include fin_first_viz.html %}

### Correlation & Regression Analysis
There is correlation

{% include fin_lin_reg.html %}

### Quartiles Analysis
Quartiles for everything

{% include fin_quartiles_box.html %}

### Checking causation
Pair matching here

{% include fin_revenue_paired.html %}

Distribution over years

{% include fin_revenue_paired_years.html %}


