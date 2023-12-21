---
layout: home
title: How Does Actor Fame Influence Movie Ratings? 
subtitle: A Datastory by Shine bright like adamon
---

- fame in terms of awards, online popularity and connections between actors


## Awarded Actors: Does the Shine of the Award Boost the Rating ?  

"Ladies and gentlemen, the Oscar for Best Actor goes to..."; have you ever heard of Meryl Streep? Or Leonardo DiCaprio? Will Smith? Yes, we bet you have. These are all Oscar-winning actors. And their movies are usually pretty successful, right? Have you ever asked yourself whether the ratings of a movie are influenced by the presence of awarded actors in them? 

In this section we ....

![award_winner](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/award_winner.png?raw=true)

### Awards Analysis
check Marine's part

{% include interactive_genre_subplots.html %}

{% include genre_distribution.html %}

## Popularity Analysis

### Rating Icons: Are the Big Names Worth the Hype ?

To understand the impact of a famous cast, we first need to define what is fame. We will consider the fame of an actor as the % of people that know the actor. Certainly, fame is subjective and context-dependent, and as much we would like to be omnipresent, our analysis will be confined to examining fame within the context of the United States of America. Now that we have our raw data, we need to take a second decision, when is someone famous? In our analysis, we will consider an actor famous only if half the US population knows him/her. Last, we need to estimate the fame of a cast ensemble, for this we will average the fame of the actors by the size of the cast. Once our measures established, we obtain the following 2 metrics per movie, the average fame of a cast, and it's famous to actor ratio (what % of the cast is famous). We find ourselves with a quantitative and a qualitative gauge for fame, now let’s see if all this reach is worth what they say.

#### Fame: Evolution Over Time

As the data we have for fame levels is actual, more recent casts should be more likely to be famous, so one could say that analysing the impact of fame wouldn’t make sense. Yet recent movies have not better ratings than old movies, we can clearly see a downward trend in average ratings over time. Not only that, but average cast fame is fairly stable after 1930’s, which let us conclude that we can interpret the effect of the fame of different casts during different periods similarly.

{% include historic_fame.html %}

### Initial Analysis

{% include initial_fame.html %}

From our visual inspection, it looks like the more famous the better the ratings are, but is it worth it? Visually, we might guess that not all levels of fame have a significant increase. As these famous cast are not free, let’s try to find more precisely at what level the difference makes sense. We will try to find which level of fame would give you the best ratings without overspending on famous cast members. In order to do this, we need to assess the impact of fame in the ratings, eliminating any possible cofounders. To isolate the effect of fame on ratings, we have performed a paired matching. In this matching, we compare movies as likely to receive our treatment, which was having a cast known on average by any % of the population. We performed a logistic regression over the size of the cast, their awards, their experience (as in how many movies they have worked on), the number of votes the movie received, the genre, language and country of origin to obtain their propensity score to be a famous cast. With the obtained group of movies to compare the effect of fame, we found no significant difference between the movies with famous and non-famous casts. Have we been lied to? No one likes movies with Brad Pitt or Meryl Streep? Maybe their success is not as consistent as we though…

![diff_means](https://github.com/thetayne/thetayne.github.io/assets/62799776/f7e59cfe-1e23-4b11-8848-fd4c2980e581)

As you can see, the previous graph contains a slider to choose what threshold is considered for the treatment of the pair matching. Play around with it. Does something stand out to you? The most curious of you, will find out that there is indeed a significant difference for a good part of the levels, just not in the direction you though. As we can see, the difference is significant for low levels of fame, indicating that you should rather have an unknown cast than a medium famous cast. On the other hand, even if we increase our treatment for only very well-known casts (average fame above 75%), the difference is very clear and still not significant. Does this mean that we should throw away our beloved star - packed casts? Not so fast my dear movie visionary, as significance depends on the result of a t-test, low density parts of the movie universe are very hard to conclude on. How many movies are they in which every cast member is known by more ¾ of the population? Not so many, therefore there is a lot of variance and very little significance to the results with this threshold, even if we would like to conclude from our initial assessment that it doesn’t make sense. With our current data, we can only conclude that we are better off with an unknown cast than with a mildly famous cast.

### But Beyond the Spotlight, Would You Rather Have Charisma or Controversy?

Is all fame good? There are multiple ways to be known, some considered more ethic than others, but does it have an impact? For this analysis, we are going to work with data concerning only the famous actors of a movie, as likeliness or controversy is much more personal and can hardly be generalized over a full cast.

{% include ratings_ratios.html %}

Our initial assessment looks like the cast with extreme values to be best suited. Indeed, a very liked cast will also be very little disliked, but yet we have some unexpected results for casts with a high dislike ratio. There is a balanced choice to make here, and maybe more to untangle than what we see. We will regress a relation between our ratios and our rating, based on the evidence that we have a correlation of value around 0.2 for each ratio with the ratings. After testing multiple models, we realized 3 key facts, errors are highly heteroskedastic, there is strict multicollinearity between our inputs and our parameters are way too big to realistically explain the impact of the ratios, therefore we need to adapt our regression. Once we obtain our model function with restricted features, penalty for large coefficients and heteroskedastic standard errors, we obtain a function with the following representation:

![graph_fct_1](https://github.com/thetayne/thetayne.github.io/assets/62799776/e74b49d6-bd37-4c79-92ae-354142f090e3)


As we can see visually, there are clearly 2 points for which our optimization could converge. Stating our constraint as forcing the ratios to sum to 1 and starting our optimization problem at random points, we obtain 2 convergences, either maximizing or minimizing likeliness. This trade off shows that there is no interest in having a neutral cast, and simulating our optimization for 100 times we obtain the following cases:

![ineqpasforce](https://github.com/thetayne/thetayne.github.io/assets/62799776/e9e4970b-3a04-4ef5-a006-e6ff237c14ec)

![force1](https://github.com/thetayne/thetayne.github.io/assets/62799776/d0faac78-28b7-493d-a2a3-adee0cad9de1)

Therefore both cases are viable options.

## Celeb Impact: How A-List Stars Affect Film Ratings

An actor can very well be Oscar-nominated or the recepient of the Emmy Award, but this does not entail that they are a Celebrity. A celebrity walks through the streets wearing sunglasses to avoid looking terrible in the paparazzi's photos. A celebrity gets stopped for pictures every time they go out in public. A celebrity knows other celebrities. A celebrity is well-connected. 

![celeb_paparazzi](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/celeb_paparazzi.png?raw=true)

Do celebrity casts increase movie ratings? 

In this section, we delve into the relationship between celebrity actors and movie ratings. We perform network analysis to evaluate the impact, if any, of different cast combinations on average movie ratings. 
Whether the actors have worked in the same genres, on movies shot in different countries, with cast-mates of similar age, let's discover if well-connected casts have an influence on movie ratings.  

### Network Analysis: The More Movies Together The Better ? 

When watching a movie, do you ever find yourself thinking: "Oh hey! These two were in that other movie together!" and wonder why? Why the same groups of actors keep being cast together? Could it be because this brings higher ratings to the movie? 
We perform network analysis, weighing edges by the number of movies that the two actors have collaborated in, to explore how they might affect each other’s impact on a movie’s rating. We identify communities among actors and analyze whether celebrity casts with actors from the same community correspond to higher movie ratings than casts with actors from across different communities. 

![actor_network_num_movies](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/actor_network_num_movies.png?raw=true)

The above graph displays the connections between actor-nodes, where the thickness of the edge-connections is proportional to the number of movie collaborations of the respective actor pairs, and the size of the actor-nodes is proportional to the average rating of the movies that the corresponding actor has been in. 

Only actors who have played in at least 15 movies were taken into account, resulting in a graph of 50 actor-nodes and 178 edge-connections. This graph is then used to identify communities of actors who often work together and to determine whether the difference in the average movie rating across communities is statistically significant. 

![community_rating_num_movies](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/community_rating_num_movies.png?raw=true)

It results that the difference in the average movie rating across communities is indeed statistically significant, with community n.6 having the highest average rating. 

### Network Analysis: Age Gap Among Actors or Not ?

Would you rather watch a movie about a group of teenagers or one about a family? The story of adult friends or that of students and their professors? This is to say: do casts of actors that are close in age perform better in terms of movie ratings than age-heterogeneous casts? 
To try to answer this question, we conduct network analysis by weighing the edges between actor-nodes by the reciprocal of the actors' age difference: the closer in age the actors are, the higher the weight of the connection. We then establish patterns and communities among the actors to explore whether taking actors from within the same community (age-homogeneous cast) results in higher movie ratings than taking actors from across different communities (age-heterogeneous cast). 

A second flavor graph was generated with 50 actor-nodes with reciprocal age difference as edge weights; the thicker the edge, the smaller the difference in age between the two actors. Similarly to the previous actor network graph, the actor-node size is proportional to the average rating of the movies that the actor has played in. A total of 8 communities of actors with similar ages who have worked together are identified on the graph and used to determine whether these exists a statistical significance for average movie ratings across communities. 

![community_rating_age](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/community_rating_age.png?raw=true)

The difference in average movie ratings across the 8 communities is found to be statistically significant, with community n.5 having the highest average rating and community n.8 having the notably lowest average rating. 

## Financial Analysis

Our focus is typically on ratings as the primary metric, but isn't the financial aspect of the movie industry just as fascinating? Is there a direct connection between movie ratings and their financial success? And do you think the fame of an actor could sway a movie's revenue potential? Let's dive in and find out!

![finance](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/finance.png?raw=true)

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

### Checking Causation

To distinguish causation from mere correlation between ratings and revenues, we calculated the propensity score for each movie, considering budget and year as potential confounders. We set the threshold for a high rating at the 50th percentile, classifying ratings above 6.5 as 'high'. This categorization yielded two groups for comparison: the treated (high rating) and the control (low rating). After pair matching based on the propensity score, the average revenues of the treatment group and the control group stood at $219,224,169.79 and $106,129,755.70. This underscores that movies with higher ratings typically garner higher revenues.

In the next graphic we visualize the average revenue of both groups, alongside their respective 95% confidence intervals.

{% include fin_revenue_paired.html %}

Afterwards, to see if there is a meaningful difference betwenn the two, a paired T-test is conducted to ascertain the statistical significance of the revenue differences between the treatment and control groups. The results confirm the significance of the disparity. Additionally, when observing the difference between the treatment and control groups over the years, we found that movies in the treatment group outperformed those in the control group revenue-wise in 93% of the years. 

Have a look below to see how treatment and control group revenues change over the years!

{% include fin_revenue_paired_years.html %}

### Results of Financial Analysis

Finalizing our financial analysis, the data presents compelling evidence that creating a movie with favorable ratings is not only artistically gratifying but is also highly likely to succeed financially, providing great rewards for the cast and directors involved.


## Conclusion
??? Let's seeeeee
