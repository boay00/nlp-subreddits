# README.md

---

# Project 3

---

## Natural Language Processing on 'superhoops' and 'LiverpoolFC' Subreddits

### Problem Statement

The '12th man' of the team is a common trope used by football pundits, which describes the enormous positive impact a strong supporting crowd can have on the performance of a Football team. Maintaining positive morale and community spirit is a vital component of sporting success. The planning committee of Queen's Park Rangers FC has requested us to look into the knock on effect of poor sporting performance and community activity.

This project looks at how a teams overall performance can effect the overall activity and language of that teams reddit community, and whether language differences caused by team scale or geography are distinguishable though the balanced accuraacy of language processing models.

---

# Important Notes

During modeling of initial tests, damage to the cpu of this machine resulted in dramtically reduced performance whilst fitting language models on large vectorised datasets. In 4-preprocessing-modeling, the code file displays the accuracy scores of the inital models before cleaning was complete, as well as accuracy scores from the same models fit with 10,000 sample observations taken from a alphabetically sorted clean dataframe. The target variable distribution was very close in comparison to the complete dataframe, however scores are obviously going to be misrepresentative of the overall complete dataframe. Once I have access to better hardware, I will update this file with the final scores. **Thanks!!**

---

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**subreddit**|object|qpr.csv|the string name of the **subreddit**|
|**body**|object|qpr.csv|the **text** body used to fit models|
|**length**|int|qpr.csv|the length of the text body in **words**|
|**score**|int|qpr_posts.csv|the number of upvotes - the number of downvotes on a post|
|**num_comments**|int|qpr_posts.csv|the **number of comments** on a post|
|**date_posted**|object|qpr_posts.csv|date that the post was made|
|**id**|object|qpr_posts.csv|the **unique id code** of the post|
|---|---|---|---|
|**subreddit**|object|liv-2.csv|the string name of the **subreddit**|
|**body**|object|liv-2.csv|the **text** body used to fit models|
|**length**|int|liv-2.csv|the length of the text body in **words**|
|**score**|int|liv-2.csv|the number of upvotes - the number of downvotes on a post|
|**num_comments**|int|liv-2.csv|the **number of comments** on a post|
|**date_posted**|object|liv-2.csv|date that the post was made|
|**id**|object|liv-2.csv|the **unique id code** of the post|

---

### Overview of Analysis

- Lots of similar words appeared in both subreddits such as: game, player, league, season etc.
- klopp (Liverpool manager) appears on the most common words for Liverpool, whilst qpr managers failed to appear on their common words list. This suggests a stronger manager to community connection when compared to qpr.
- Interestingly, goal appears in the top words in the Liverpool subreddit, but does not in QPRs. This may be because of a lack of comment data from liverpools subreddit. Goal would likely appear in main posts more frequently than comments.
 --- 
- Liverpool subreddit has a much higher percentage of posts with 4 of the 5 swear words. 'Crap' is however more commonly used in the qpr subreddit. This may be a result of dialect differences between northern and southern fanbases. These results are taken from purely post data, excluding comments.
- The expectation of including comments in the data was that the occurence of swearing would increase. When compared to the data from only main posts, we can see that the level of swearing is much more comparable between the two subreddits. Decreased exposure to readers when commenting may remove some of the filter for inappropriate language, increasing the occurence. Pulling extra data from liverpool comments would be interesting to investigate this trend.
---
- Liverpool Average number of posts per year increases until 2018, and steadily decreases afterwards, data from 2023 is not reliable since only a few months have passed.
- Improved team performances generally correlate with an increase in total yearly posts in the liverpool instance. Perhaps prolonged success could be causing a drop in community activity however there may be many factors causing this decline.

- Relative success for QPR between 2011 and 2015 also is shown to be the most active years for this subreddit. 2011 is low because not only was the subreddit new, but reddit in general was not a popular resource.
- Relegation in 2015 clearly reduced community activity and post quantities have never fully recovered since QPRs time in the Premier League (1st division). The most active year was a year in the championship (2nd Division) in 2014, however this season was a year of high win percentage when compared to low finishes in the top division, so increased activity is likely.
---
- Unlike the overall activity, there does not seem to be a trend in the post approval with team performance in the QPR subreddit. 
- There is a strong match in the trend for the liverpool subreddit, however the upvote trend is very similar to the qpr subreddit trend, so it cannot be confirmed that the improved team performance is causing this.
- Strangely, the qpr subreddit drops in average upvote score in 2022, perhaps due to a subduing in community activity for this subreddit. Years spanning the SARS-CoV-2 pandemic coincide with the highest average post score, perhaps caused by an increase in online viewing of sport during this period.
---
- The liverpool average word count has decreased over the last decade, particularly dropping during the years of success in 2018 - 2022. Perhaps increased influx of new fans in this time wanting to post simpler picture posts of iconic goals or moments in this period is causing this.
- Otherwise, years of struggle for liverpool (pre 2017) would be a time of increased anguish in the community, leading to longer and more opinionated posts. 
- This data is not reliable, since all posts below 10 words in length have been filtered out. One of these subreddits may have a huge number of these posts, which would massively reduce the average word count.

---

# Conclusions

Despite having little attention directed to cleaning of special characters, numbers, non english words and spam posts, these models generally performed well in terms of balanced accuracy. They all successfully outperformed the null model, but particularly effective models were Multinomial Naive Bayes and a stacking model combining Logistic regression, BernoulliNB and MultinomialNB. On unclean data, these models achieved a balanced accuracy of 92.4%, as well as scoring 83.5% on a small sample of clean data.

With greater computational power, I believe the MultinomialNB and stack models would have produced very strong balanced accuracy scores on fully cleaned data, and would have therefore been very effective in predicting the original subreddit for a body of text. 

These findings show that despite the similarity in these subreddits, the language used is distinct enough to successfully distinguish and hence correctly predict the original subreddit with very high accuracy. 

##### Further Conclusions

- The success of a football team generally has a positive impact on community activity and post frequency.
- Larger teams are likely to have a more toxic community in terms of swear words used per post than smaller teams. There are exceptions to this however, since some words are more commonly used in certain dialects. 
- In general, increased success of a team results in a lower post length on average.
- Language models are shown to be able to predict the original subreddit of a text body with high accuracy, despite initial predictions suggesting that the language used would be too similar to form clear distinctions.

# Recommendations

- Collecting data proved to be challenging, since Liverpools subreddit was so large, and QPRs was so small. Collecting comments from Liverpools subreddit would result in too large a data imbalance, but would be required to reliably compare language across all types of text body. Certain language is more likely in comments than in prose paragraphs or titles. Despite this, the choice to only use first level comments would have reduced this, since reactions to comments are likely contributing to differences in language used the most.

- Comparing language used with a focus on dialect differences would be an interesting follow up route, which was breifly introduced upon inspection of swear word frequency.