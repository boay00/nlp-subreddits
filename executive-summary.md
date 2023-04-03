# Executive Summary

In order to examine the nuances in language use between two online football communities, we have been tasked with analysing data from QPR and Liverpool Subreddits. Information derived from this study can be passed onto corporate boards of all football teams, but has been specially requested by Queen's Park Rangers to determine any knock on effects caused by ever worsening domestic results on the supporters community. This project compares the subreddits of a European giant, Liverpool FC with the comparatively small 'superhoops' subreddit, and aims to produce an effective Natural Language Processing model capable of distinguinshing between these subreddits, whilst accurately determining the subreddit origin of a post or comment.

Data was pulled through the Pushshift API then cleaned and analysed through various visualisations. Text data was then pre processed and fit with a variety of machine learning classification models. These models were evaluated by assessing their balanced accuracy score.

Overall, the strongest models were found to be Multinomial Naive Bayes, as well as a Stacked model which incorporated various other models previously fitted to the data.

Many insights were gathered from the cleaned data, particular focus was put on overall activity, measured in total posts across all years. It was found that strong performances generally correlate with a higher community activity, and vice versa. It was also found that a teams success correlates with a decrease in the average post length.

Upon closer inspection of the text data, stronger language is more prevelant in stronger teams communities and differenes in dialect are able to be identified if given sufficient attention. This concept may be an interesting idea to follow up on in the future.

Whilst optimisation is of course possible, the models produced show great potential for classification and prediction.
