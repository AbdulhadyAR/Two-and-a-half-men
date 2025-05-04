# Charlie's Gone, But the Show Went On: A Data-Driven Analysis of the Kutcher Transition in "Two and a Half Men"

![photo](/assets/img/Two-and-a-Half-Men.jpg) 
Warner Bros Tv/Chuck Lorre Prod/Kobal/Shutterstock

#### CBS aired the very successful sitcom "Two and a Half Men" from 2003-2015 with the plot centering around the life of carefree bachelor Charlie Harper (performed by Sheen), whose calm existence gets turned upside down when his divorced brother Alan (Cryer) and nephew Jake (Jones) move in with him. The show became a cultural phenomenon, running for 12 seasons.

#### An unprecedented event occurred in 2011 when Sheen was dismissed from the show due to public controversies (US Magazine). A new lead character played by Ashton Kutcher was later introduced. The natural experiment in television was put into place: what happens to a show's success when the lead actor is replaced? This project seeks to answer that using data science and machine learning approaches.

## Data Collection and Preparation
Because there were no datasets available for immediate use, I collected data from IMDb that had episodes rating and users reviews. With the Selenium library, I scraped the following two essential key components from the site:

1. **Episodes rating:** Each record contains the episode title, episode description, season and episode number, average rating, vote count, and air date.

2. **User reviews:** Unstructured textual feedback containing review title, review text, rating (if provided), and date posted.

I prepared the raw scraped data by cleaning and organizing it into structured CSV files to ensure consistency for subsequent statistical and textual analysis.

[Link to the Tableau visualizations](https://public.tableau.com/views/Twoandahalfmen/Sheet1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

## IMDB ratings over the show
![Average ratings by season](/assets/img/avg-ratings-by-season.png) 

The series maintained impressive ratings above 7.5 through Sheen's eight season period. After his departure and Ashton Kutcher’s arrival in Season 9, the ratings fell to 6.0 with some temporary recovery before ultimately dropping to 5.4 during the show’s last season. This pattern of rating changes aligned with the change in lead actors with a clear dip in audience appreciation in the later seasons.

![Average ratings by episode](/assets/img/avg-ratings-by-episode.png) 

The rating patterns of the episodes indicate differences between the two periods. Sheen’s performances varied from a series low of 7.1 in Episode 5 to a high of 8.2 in his final episodes. Kutcher’s episodes started with a series low of 5.75 in Episode 5 and climbed to 6.73 in Episode 19, still considerably lower than Sheen’s average. The information captures a striking gap in ratings between the two leads’ periods.

## Votes over the show
![Median of votes by season](/assets/img/median-of-votes-by-season.png) ![Median of votes by episode](/assets/img/median-of-votes-by-episode.png) 

The data shows a drop in the median votes for later seasons, with the lowest numbers aligning with Kutcher’s tenure and Sheen’s exit. While Sheen’s episodes received higher vote counts, the subsequent seasons maintained a lower voter turnout. This indicates reduced voters’ attention during the later years of the show, however there are several reasons that could be attributed to the change.

## Ratings vs Votes
![Ratings vs votes ](/assets/img/ratings-vs-votes.png) 


The graph shows Kutcher's episodes attracted the highest vote counts, with notable spikes occurring during two key moments: his debut episode and his final appearance in the series finale.

![Highest number of votes ](/assets/img/highest-votes.png) 

These peaks in viewer participation frame his tenure on the show, marking both his introduction and departure as particularly engaging moments for the audience.

## User reviews
![neurtal reviews](/assets/img/neutral-reviews.png) ![positive reviews ](/assets/img/positive-reviews.png) 

Examining the review word clouds shows some viewer sentiment patterns. In the neutral reviews, “bring back, without, left, and ruined” stand out as common phrases which may mirror audience sentiments regarding the cast change. On the other hand, positive reviews feature “Charlie” as the most prominent keyword which indicates strong associations from the viewers during his run on the show.

## Decision Tree Regressor

Decision trees can effectively predict numbers like TV ratings by finding patterns in data. The model works by repeatedly splitting the data into groups based on important factors.

For this project, I built a decision tree to guess episodes rating. First, I removed:

Actual ratings (predicted value)

Text lengths (low relevance)


![Result](/assets/img/decision-tree-result.png) 

The model performed well at guessing ratings. The below image shows how the predicted points are close to the line which represents the actual values. While these results look good, I'll test other methods to find the best approach.

![Actual vs Predicted](/assets/img/actual-vs-predicted.png) 

## Random Forest vs. XGBoost: Which Did Better?

Random Forest and XGBoost are both powerful ensemble methods that combine multiple decision trees to improve predictions. Random Forest builds independent trees and averages their results, while XGBoost sequentially improves trees by learning from previous errors.

![Actual vs Predicted](/assets/img/rf-vs-xgb.png) 

In our tests, Random Forest captured slightly better overall trends (R² 0.9039 vs 0.8999), while XGBoost delivered marginally more precise individual predictions (MAE 0.1982 vs 0.2038). The choice depends on whether you prioritize broad pattern recognition or exact rating estimates.

![Feature importance](/assets/img/feature-importance.png) 


The figure above explains seasons and cast changes (like Charlie Sheen's presence) are the biggest rating predictors. While vote counts have some influence, episode numbers contribute little - we might remove this feature to boost accuracy, but we have to proceed carefully to avoid overfitting the model to our specific dataset.

## Sentiment Classifier

To analyze viewer sentiment, I developed a classification system comparing four machine learning approaches:

Logistic Regression - A linear model estimating positive/negative probability.

Naive Bayes - Applies probability theory with feature independence assumption.

SVM (Support Vector Machine) - Creates optimal decision boundaries in high-dimensional space.

Neural Network - Deep learning model detecting complex sentiment patterns.

![Sentiment classifier result](/assets/img/sentiment-classifier-results.png) 


According to the analysis, logistic regression achieves the highest accuracy of 83%, alongside F1 scores of 0.87 and 0.83 for neutral and positive sentiments, respectively. Although Naive Bayes performs better with negative sentiments (F1=0.71) and SVM performs better with neutral recall (96%), all models struggle with detecting negative sentiment, ranging from 30-60% recall.

![confusion matrix](/assets/img/confusion-matrix.png) 

Logistic regression emerges as the preferred default choice, with potential adjustments to class weighting for improved negative detection. The consistent challenges with negative sentiment classification across models may indicate underlying dataset limitations.

## Final Say: The Numbers Don’t Lie

The figures tell a story: Two and a Half Men was exceptionally successful with Sheen as the lead, maintaining consistent high ratings and viewer engagement. His departure coincided with a drop in ratings; though Ashton Kutcher's addition sparked short-lived interest (as indicated by the vote spikes), the show never regained its charm. In Season 9, ratings dropped by 20% and settled at 5.4 by the series finale.

Machine learning models revealed what loyal fans already knew: cast and season changes were the show's biggest predictors of success, far outweighing everything else. Random Forest proved better than XGBoost at capturing trends (R²=0.90), and through sentiment analysis, it was clear that fans still held affection for Sheen (the name “Charlie” came up most among positive reviews). While the show was able to survive post-Sheen, data indicates that some chemistry cannot be duplicated.

This work demonstrates the power of data science in analyzing shifts in culture—and shows how, even in the entertainment world, statistics often reveal the unfiltered truth.

## Reference
[Two and a Half Men - IMDB](https://www.imdb.com/title/tt0369179/reviews/?ref_=ttep_ql_2)

[Charlie Sheen and Chuck Lorre’s Ups and Downs After ‘Two and a Half Men’ Firing, ‘How to Be a Bookie’ Reunion](https://www.usmagazine.com/celebrity-news/pictures/two-and-a-half-mens-charlie-sheen-chuck-lorres-ups-and-downs/)



