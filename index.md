---
layout: home
title: How Does Actor Fame Influence Movie Ratings ?
subtitle: A Datastory by Shine Bright Like Adamon
cover-img: /assets/img/background.png
thumbnail-img: /assets/img/background.png
share-img: /assets/img/background.png
use-site-title: true
---

In the glitzy world of Hollywood, fame and fortune are everything. From the choice of the cast, to the country of production, to the outfit worn at the 56th minute, everything is done in order to maximize a movie's success. But in the 21st century, where an actor's Instagram following can earn them thousands of dollars per sponsored post, and where users can access the profiles of an actor's castmates and of their movie with just a few cliks, does fame have an impact of movie ratings? What about online popularity? Maybe these aspects overshadow the influece of renouned awards... **The more famous actors in a movie, the better the ratings?** 

Let's find out! 

![line](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/line.png?raw=true)

Join us as we embark on a cinematic odyssey, from the glitzy world of Oscar awards to the vibrant realm of online popularity. We'll venture deep into the heart of actor communities, where connections and collaborations are forged, all in pursuit of uncovering the tantalizing secrets that may shape movie ratings.

But that's not all! Hold on tight as we set out to discover whether fame, that elusive shimmering starlight, holds the key to blockbuster revenue. The silver screen awaits, and we're about to unravel the thrilling mysteries that make the movie industry sparkle. 

And while you do so, enjoy some DALL-E generated cartoons and take a moment to appreciate the power of Applied Data Analysis: from a dataset to a data story, discover the magic of turning numbers into narratives, and Shine bright like a... Star!

## Awarded Actors: Does the Shine of the Award Boost the Rating ?  

"Ladies and gentlemen, the Oscar for Best Actor goes to..."; have you ever heard of Meryl Streep? Or Leonardo DiCaprio? Will Smith? Yes, we bet you have. These are all Oscar-winning actors. And their movies are usually pretty successful, right? Have you ever asked yourself whether the ratings of a movie are influenced by the presence of awarded actors in them? 


![award_winner](https://github.com/thetayne/thetayne.github.io/blob/master/_includes/award_winner.png?raw=true)


This analysis will focus on the impact of Oscar awards on movie ratings. Let's first explain how we define an "award", we consider both nominees and winners of the Oscars. In fact, we believe that a nomination itself is indicative of a significant acting talent. The chosen time frame for the study starts from movies released in 1926 and onwards. This starting point is selected to coincide with the Oscars' inception in 1927, providing a historical and comprehensive dataset. To deepen our understanding, we measure the total number of Oscars won by the entire cast of each movie prior to its release. Additionally, we calculate the average number of awards per actor within the movie. 

#### Distribution of Votes: Is It Fair to Compare a Blockbuster to an Obscure Gem?

We first chose to ask ourselves: Is it fair to compare a blockbuster to a niche movie seen by few people? To respond we looked at the distribution of the number of votes leading to the average rating calculation for a movie. This allows us to make sure that the rating accurately represents the true opinion of the audience. 

{% include votes_analysis.html %}

In our original data set we had approximately 21,000 movies, looking at the graph we observe a significant skew in the distribution of votes, with over 14,000 movies receiving 2,000 votes or fewer. This initial finding suggests a concentration of movies with minimal public interaction, most of which lacked any Oscar awards. However, movies with a very low number of votes may not have a statistically reliable average rating. Therefore, keeping those movies would lead to false conclusions as a movie with 10 votes will be compared in our analysis to movies with more than 100k votes. 

To ensure the integrity and relevance of our analysis, we established a threshold of 2,000 votes. Movies with votes below this threshold were considered to potentially skew the results due to the lower level of viewer engagement and the absence of awards. Subsequently, we refined our dataset to focus on the 7’070 movies that surpassed this vote count, which provides a more reliable foundation for evaluating the impact of Oscar awards on movie ratings.

The first thing we wanted to visualize is a possible trend between the average IMDB rating and the number of awards within the cast. 

{% include interactive_movie_analysis.html %}

At first glance, the data points suggest a potential relationship between the two variables, but the correlation is not immediately clear due to the dense clustering of data across the range of award counts. The plot shows movies with varying numbers of awards distributed across the entire spectrum of IMDb ratings, from low to high. Notably, the data density does not allow for an easy visualization of a distinct trend. This suggests that while there may be a correlation, the relationship is not straightforward and could be influenced by other factors.

#### The Interplay of Oscars and Ratings Across Genres

Given the lack of categorization of the data, we wanted to try and see if there was any difference in trend depending on the genre of the movie. Does a high number of awards within the cast of an action movie lead to a higher rating? Is a comedy movie better ranked when the cast isn’t rewarded by the academy? Does it change in time? This additional layer of categorization could help to clarify the influence of awards on ratings within specific types of movies, allowing for a more nuanced understanding of how the Oscars affect different segments of the film industry. Because of the very high number of possible genres, we chose to continue the analysis taking into account only the five more populated genres which are "Drama", "Comedy", "Thriller", "Romance Film" and "Action".

{% include interactive_genre_subplots.html %}

From our graphs, we see that all trends seem similar, therefore they might not be significantly impacted by the genre of a movie. This visualization however helps us visualize further a possible correlation between the average rating of a movie and the numbers of awards within the cast. Therefore, no matter the genre, an award-winning cast does seem to increase the chance of having a higher rating! 

#### The Actor’s Career: Can an Oscar Nomination Guarantee Higher Movie Ratings?

The lingering question is: What is the effect of academic recognition on an actor's career? Does it impact the ratings of the movies that follow? Is an Oscar nomination a golden ticket to better movie ratings or just a pat on the back for the already talented? To answer these questions, we’ve plotted the average ratings of the movies they starred in, relative to their award history. We track the movies' ratings before and after the actors were nominated to the Oscars to discern any trends in how their recognition at the Oscars might affect the perceived quality of their films.

{% include avg_award.html %}

We can observe that, while some might climb to the top after an award, others wobble, and a few even take a dip. However, the overall trend is steady. This would mean that a good actor that got praised academically in the future was just as good in his debut! 

#### From Visual Trend-Spotting to Predictive Modeling

Our initial visual analysis indicates that there is indeed a better chance of have higher rating if you work with an award winner. However, hiring such an actor is expensive so we'd better look more precisely into this! Through the initial visual analysis, we've sifted through the distribution of votes to refine our dataset, explored chronological trends, dissected genre-specific nuances, and traced the trajectories of individual actors' careers in relation to their awards. Now, we advance to a critical juncture in our visual exploration: prediction using Ordinary Least Squares regression. This predictive analysis employs OLS to draw potential correlations from our existing data visually. It serves as an intermediary step, harnessing our findings to model the expected relationship between awards and movie ratings.

{% include prediction_analysis.html %}

From visual inspection, it looks like the higher the number of awards the higher the rating, but is it truly the case? In both analyses, the positive linear relationship of the equations implies that, as the number of awards (the average or the total) increases, there is a positive effect on the average rating of the movie. However, in both analyses, the low R-squared value suggests that there is little meaningful linear correlation between the average rating of movies and the number of nominations in the cast. In other words, the analysis does not provide strong evidence that an increase in awards, both in the average over the cast and in the total count, significantly affects the average rating of the movies. Therefore, based on these results, it seems like any relationship that exists is likely weak or influenced by other factors not considered in this analysis.

#### Correlation and Paired Matching Analysis

To further investigate the correlation between the number of awards nominees in the cast and the average rating of the movie, we used Pearson’s correlation coefficient to mesure the strength and direction of the relationship. In this case, the calculated correlation coefficient is 0.13, indicating a positive correlation between the cumulative count of awards won by the cast and the average ratings of movies. This suggests that as the cumulative count of awards increases, there is a tendency for movies to receive higher average ratings. This is a good start! However, we need to look in details at the possible confounders. In fact, the size of the cast, their fame percentage and experience, the number of votes the movie received, the genre, language and country of origin might be impacting our analysis! To resolve this issue, we needed to isolate the possible effect of the number of nominations on the average rating of a movie. Therefore, we chose to perform pair-matching. Because we want to look at the results of an overall academically rewarded cast, we chose to take all the movies with at least 11 nominations as our treatment. We then performed a logistic regression over all the possible confounder variables stated before to obtain the propensity score of being an award-winning cast. Now let’s see, is it worth it to pay a higher prize for an academically gifted cast? 

![paired_11](https://github.com/thetayne/thetayne.github.io/assets/100578052/52166593-b409-4b23-ac18-6f5781a5cb95)


We can observe, that because the obtained t-statistic is positive, the difference in means is statistically significant. Furthermore, the p-value is below the significance level (0.05), therefore, the average ratings for movie with at least 11 award winner is higher! Finally, we performed a linear regression over the matched pairs to examine the relationship between the average rating of movies and the cumulative count of awards won by the cast. We found an R-squared value of 0.107 indicating that approximately 10.7% of the variability in movie ratings can be explained by the cumulative count of awards won by the cast. However, this relationship explains only a relatively small portion of the variation in ratings, highlighting the multifaceted nature of factors that contribute to a movie's success and reception.

We can therefore conclude that assembling a cast full of Oscar’s nominees is a good idea to increase your ratings, but you might want to also look at other aspects of a movie realization that might have a more significant impact for your goal to achieve higher ratings! 



## Online Popularity: Are the Big Names Worth the Hype ?

In this section, we rescind our understanding of fame to the online popularity of a cast. To understand the impact of a famous cast, we first need to define what is fame. We consider the fame of an actor as the % of people that know the actor. Certainly, fame is subjective and context-dependent, and as much we would like to be omnipresent, our analysis is confined to examining fame within the context of the United States of America. Now that we have our raw data, we need to make a second decision: when is someone famous? In our analysis, we consider an actor to be famous only if half the US population knows him/her. Lastly, we need to estimate the fame of a cast ensemble, for this we average the fame of the actors by the size of the cast. Once our measures established, we obtain the following 2 metrics per movie, the average fame of a cast, and its famous to actor ratio (what % of the cast is famous). We find ourselves with a quantitative and a qualitative gauge for fame, and now let’s see if all this reach is worth what they say.

#### Fame: Evolution Over Time

As the data for fame levels is actual (scrapped in October 2023), more recent casts should be more likely to be famous, so one could say that analysing the impact of fame over casts from different periods wouldn’t make sense. Despite the fact that we have an increase in the number of famous cast movies, the average cast fame is fairly stable after 1930’s, which lets us conclude that we can interpret the effect of the fame of different casts during different periods in a similar manner. Not only that, but recent movies do not have better ratings than old movies; on the contrary, we can clearly see a downward trend in average ratings over time, showing how being famous is not as influential or likely nowadays as we might have thought.

{% include historic_fame.html %}

### Initial Analysis

{% include initial_fame.html %}

From our visual inspection, it looks like the more fame the better the ratings are, but is it worth it? Visually, we might guess that not all levels of fame have a significant increase. On the other hand, the impact of the ratio doesn’t look very meaningful. As these famous casts must be adeguately compensated, let’s try to find more precisely at what level the difference makes sense. We will try to find out which level of fame would give you the best ratings without overspending on famous cast members. In order to do this, we need to assess the impact of fame in the ratings, eliminating any possible confounders. To isolate the effect of fame on ratings, we performed paired matching. In this matching, we compare movies equally likely to receive our treatment of having a cast known on average by any % of the population. We performed a logistic regression over the size of the cast, their awards, their experience (as in how many movies they have worked on), the number of votes the movie received, the genre, language and country of origin to obtain their propensity score to be a famous cast. With the obtained group of movies to compare the effect of fame, we found no significant difference between the movies with famous and non-famous casts. Have we been lied to? No one likes movies with Brad Pitt or Meryl Streep? Maybe their success is not as consistent as we though…

![reg_0](https://github.com/thetayne/thetayne.github.io/assets/62799776/600f8479-b9d3-4a7a-8a42-0a909d77a899)

What if we evaluate each level of fame? Is there any threshold for which the difference is significant?

![ada_gif](https://github.com/thetayne/thetayne.github.io/assets/62799776/bf103324-a2ea-4ab4-986c-6b826bd9c3ac)

As you can see from the animation graph, we evaluate the difference for every threshold, and can observe the it in the conclusion graph just below. Does something stand out to you? The most curious of you will spot that there is indeed a significant difference for an important part of the levels, just not in the direction you might have predicted. As shown in the summary graph below, the difference is significant for low levels of fame, indicating that you should rather have an unknown cast than a medium famous cast. On the other hand, even if we increase our treatment for only very well-known casts (average fame above 75%), the difference is very clear and still not significant. Does this mean that we should throw away our beloved star-packed casts? Not so fast my dear movie visionary, as, since significance depends on the result of a t-test, low density parts of the movie universe are very hard to conclude on. How many movies are there in which every cast member is known by more ¾ of the population? Not so many, therefore there is a lot of variance and very little significance to the results with this threshold, even if we would like to conclude from our initial assessment that it doesn’t make sense. With our current data, we can only conclude that we are better off with an unknown cast than with a mildly famous cast.

![diff_means](https://github.com/thetayne/thetayne.github.io/assets/62799776/f7e59cfe-1e23-4b11-8848-fd4c2980e581)


### But Beyond the Spotlight, Would You Rather Have Charisma or Controversy?

Is all fame good? There are multiple ways to be known, some considered more ethic than others, but does it have an impact? For this analysis, we are going to work with data concerning only the famous actors of a movie, as likeliness or controversy is much more personal and can hardly be generalized over a full cast.

{% include ratings_ratios.html %}

Our initial assessment is that the cast with extreme values is the best suited. Indeed, a highly-liked cast will also be very little disliked, and yet we have some unexpected results for casts with a high dislike ratio. There is a balanced choice to make here, and maybe more to untangle than what we can see. We will regress a relation between our ratios and our rating, based on the evidence that we have a correlation of value around 0.2 for each ratio with the ratings. After testing multiple models, we realized 3 key facts: errors are highly heteroskedastic, there is strict multicollinearity between our inputs, and our parameters are way too big to realistically explain the impact of the ratios, therefore we need to adapt our regression. Once we obtain our model function with restricted features, penalty for large coefficients and heteroskedastic standard errors, we obtain a function with the following representation:

![graph_fct_1](https://github.com/thetayne/thetayne.github.io/assets/62799776/e74b49d6-bd37-4c79-92ae-354142f090e3)

As we can see visually, there are clearly 2 points for which our optimization could converge. Stating our constraint as forcing the ratios to sum to 1 and starting our optimization problem at random points, we obtain 2 consistently convergences, either maximizing or minimizing likeliness. This trade off shows that there is no interest in having a neutral cast, and, simulating our optimization for 100 times, we obtain the following cases:

![ineqpasforce](https://github.com/thetayne/thetayne.github.io/assets/62799776/e9e4970b-3a04-4ef5-a006-e6ff237c14ec)

It becomes clear that both options are suitable for a great success in ratings. SInce the type of cast is highly heterogeneous, it should be studied with caution for each specific case. It is also worth mentioning that this should be a minor concern when picking the cast, as the explanatory power of our model is small.

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

### Network Analysis: Do People Like Actor Diversity? 

The previous result brings up another question revolving aroung the same idea, but this time analyzing the the diversity of the cast in terms of community membership: how does the diversity of the cast influence the movie rating? To thoroughly analyze this question we will define diversity in 3 different ways. Let $n$  b the number of communities and $P(x_i)$ be the proportion of actors in the $i^{th}$ community relative to the total number of actors in a movie. Then we define diversity in the following 3 ways:

**1. Shannon Entropy:** Entropy in this context quantifies how evenly spread the cast members are across different communities. A lower entropy value would suggest that most cast members come from the same or a few communities (more uniform), while a higher value indicates a more diverse cast across many communities. The shannon entropy of the distribution of actors across communities in a movie is defined as
$$ H(X) = -\sum_{i=1}^{n} P(x_i) \log_2 P(x_i) $$

**2. Gini-Coefficient:** Originally used to measure income inequality, the Gini coefficient can be adapted to measure inequality in community representation within a movie's cast. A Gini coefficient of 0 would indicate perfect uniformity (all cast members are from the same community), while a coefficient closer to 1 would indicate high inequality (cast members are evenly spread out across many communities).
For a discrete probability distribution, the formula for the Gini coefficient can be simplified to
$$ G = 1 - \sum_{i=1}^{n} P(x_i)^2 $$

**3. Binary-Diversity Indicator (BNI):** In contrast to the other measures the BNI is binary and first and foremost more straight forward to interpret, which is why we included it in our analysis as well. If more than 70% of all considered actors come from the same community, we consider the cast as not being diverse.

In order for these measures to be meaningful, we exclude movies which only contain one actor, seen as they would affect the results by not being labelled as diverse but only because a single actor plays in them. First, let's look into our continuos diversity measures, namely the entropy and the Gini coefficient. To begin, let's have a look at a histogram to get an idea of the distribution of our diversity measures.

    TODO INCLUDE INTERACTIVE HISTOGRAM (WOULD BE NICE WITH OVERLAY OF BOTH DISTRIBUTIONS INSTEAD OF BUTTON SWITCH) entropy/gini-frequency

While at first sight the diversity in terms of entropy and the Gini coefficient seems similar, with most movies having a non-diverss cast and a similar-looking distribution for non-zero measures, the scale of both is actually different.

In order to figure out the right type of regression based on the relationship of the diversity to the average movie ratings, we use the scatterplot below.

    INCLUDE INTERACTIVE SCATTERPLOT showing entropy /gini-averageRating

There seems to be no obvious relationship present between our continuos diversity measures and the average rating. As expected, a linear regression therefore returns statistically non-significant coefficients (p-values are 0.15 and 0.29) while also the R-squared values are extremely small (0.002 and 0.001). The variance in the movie ratings is hence not explained by our continuos diversity measures.

We will see that unsurprisingly the same holds for our BNI measure. Regarding BNI we end up with 715 movies that have a diverse cast and 1498 that have a non-diverse cast, as seen below in the diagramm.

    POTENTIALLY INCLUDE BAR DIAGRAMM OF BNI

To be statistically correct for the binary BNI we first do both paired and propensity score matching to account for potential confounders before performing a linear regression. Potential confounders influencing both the diversity of the cast and the ratings are the number of languages, the number of countries, the release year and the genre of the movie. After matching, we are left with a balanced dataset of 318 movies. When comparing the average rating of diverse and non-diverse casts for our balanced and unbalanced dataset there is barely a difference. Equal to our observations with the continuos diversity measures above, the linear regression is not statistically signifant and does not explain the underlying data well as indicated by an R-squared of 0.

To conclude our analysis of the influence of the cast-diversity on the movie ratings, we didn't observe any statistically significant effect. The diversity measure does not explain the variability in movie ratings. Viewers do not seem to care about how often the actors collaborate or how similar they are in terms of done movies; they rather evaluate a movie based on other criteria.

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

Afterwards, to see if there is a meaningful difference between the two, a paired T-test is conducted to ascertain the statistical significance of the revenue differences between the treatment and control groups. The results confirm the significance of the disparity. Additionally, when observing the difference between the treatment and control groups over the years, we found that movies in the treatment group outperformed those in the control group revenue-wise in 93% of the years. 

Have a look below to see how treatment and control group revenues change over the years!

{% include fin_revenue_paired_years.html %}

### Results of Financial Analysis

Finalizing our financial analysis, the data presents compelling evidence that creating a movie with favorable ratings is not only artistically gratifying but is also highly likely to succeed financially, providing great rewards for the cast and directors involved.


## Conclusion
??? Let's seeeeee
