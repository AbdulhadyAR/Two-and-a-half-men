# Charlie's Gone, But the Show Went On: A Data-Driven Analysis of the Kutcher Transition in "Two and a Half Men"

![photo](/assets/img/Two-and-a-Half-Men.jpg) 
Warner Bros Tv/Chuck Lorre Prod/Kobal/Shutterstock

#### "Two and a Half Men" was a wildly popular CBS sitcom that followed the life of Charlie Harper (Charlie Sheen), a carefree bachelor whose lifestyle is disrupted when his divorced brother Alan (Jon Cryer) and nephew Jake (Angus T. Jones) move in with him. The show became a cultural phenomenon, running for 12 seasons from 2003 to 2015.
#### The series faced an unprecedented challenge in 2011 when Charlie Sheen was dismissed following public controversies (Source: US Magazine). Ashton Kutcher joined as a new lead character, creating a natural experiment in television - how does replacing a lead actor impact a show's success? This project employs data science and machine learning techniques to quantify that impact.

## Data Collection and Preparation
Since no ready-to-use datasets were available, I conducted primary research by gathering data from IMDb, which contained episodes rating and user reviews. Using the Selenium library, I scraped two key components from the website:
#### 1. Episode ratings: Each entry includes the episode title, episode description, season and episode number, average rating, vote count, and air date. 
#### 2. User reviews: Unstructured textual feedback containing review title, review text, rating (if provided), and date posted. 
The raw scraped data was cleaned and formatted into structured CSVs, ensuring consistency for further statistical and textual analysis.

[Link to the Tableau visualizations](https://public.tableau.com/views/Twoandahalfmen/Sheet1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

## IMDB ratings over the show
![Average ratings by season](/assets/img/avg-ratings-by-season.png) 

The show maintained consistently strong ratings above 7.5 during Charlie Sheen's eight-season tenure. Following his departure and Ashton Kutcher's arrival in Season 9, ratings fell to 6.0, with a temporary rebound before ultimately declining to 5.4 in the final season. This rating pattern coincided with the lead actor transition, showing a notable shift in audience reception during the later seasons.

![Average ratings by episode](/assets/img/avg-ratings-by-episode.png) 

The episodes rating show distinct patterns between the two eras. Sheen's performances ranged from a series-low of 7.1 (Episode 5) to a peak of 8.2 in his final episodes. Kutcher's episodes opened at a series-low of 5.75 (Episode 5) before recovering to 6.73 (Episode 19), still significantly below Sheen's average performance. The data reveals a notable rating differential between the two leads' tenures.

## Votes over the show
![Median of votes by season](/assets/img/median-of-votes-by-season.png) ![Median of votes by episode](/assets/img/median-of-votes-by-episode.png) 

The data reveals a decline in median votes during the later seasons, with noticeably lower numbers coinciding with Kutcher's arrival and Sheen's departure. While Sheen's episodes maintained higher vote counts, the post-transition seasons saw a sustained reduction in voter participation. This pattern suggests decreased viewer engagement during the show's later years, though multiple factors could contribute to such trends.

## Ratings vs Votes
![Ratings vs votes ](/assets/img/ratings-vs-votes.png) 


The graph shows Kutcher's episodes attracted the highest vote counts, with notable spikes occurring during two key moments: his debut episode and his final appearance in the series finale.

![Highest number of votes ](/assets/img/highest-votes.png) 

These peaks in viewer participation frame his tenure on the show, marking both his introduction and departure as particularly engaging moments for the audience.

## User reviews
![neurtal reviews](/assets/img/neutral-reviews.png) ![positive reviews ](/assets/img/positive-reviews.png) 

The analysis of the review word clouds reveals distinct patterns in viewer sentiment. In neutral reviews, prominent terms like "bring back," "without," "left," and "ruined" frequently appear, potentially reflecting audience reactions to the cast transition. Meanwhile, positive reviews show "Charlie" as the most dominant word, suggesting his strong association with favorable viewer perceptions during his tenure on the show.

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


The evaluation shows logistic regression performs best overall with 83% accuracy and strong F1 scores for neutral (0.87) and positive (0.83) sentiments. While Naive Bayes handles negative reviews slightly better (F1=0.71) and SVM excels at neutral recall (96%), all models struggle with negative sentiment detection (30-60% recall).

![confusion matrix](/assets/img/confusion-matrix.png) 

Logistic regression emerges as the preferred default choice, with potential adjustments to class weighting for improved negative detection. The consistent challenges with negative sentiment classification across models may indicate underlying dataset limitations.

## Final Verdict: The Numbers Don’t Lie

The data paints a clear picture: Two and a Half Men thrived under Charlie Sheen’s lead, with consistently high ratings (7.5–8.2) and strong viewer engagement. His departure marked a turning point—while Ashton Kutcher’s arrival brought temporary curiosity (evidenced by vote spikes), the show never fully recovered its original appeal. Ratings dropped by 20% in Season 9 and continued to decline, settling at 5.4 by the finale.

Machine learning models confirmed what fans felt: seasons and cast changes were the top predictors of success, far outweighing other factors. Random Forest outperformed XGBoost in capturing trends (R²=0.90), while sentiment analysis revealed lingering nostalgia for Sheen (the word "Charlie" dominated positive reviews). Though the show survived the transition, the data suggests some chemistry is simply irreplaceable.

This project highlights how data science can decode cultural shifts—proving that even in entertainment, numbers often tell the most honest story.

## Reference
[Two and a Half Men - IMDB](https://www.imdb.com/title/tt0369179/reviews/?ref_=ttep_ql_2)

[Charlie Sheen and Chuck Lorre’s Ups and Downs After ‘Two and a Half Men’ Firing, ‘How to Be a Bookie’ Reunion](https://www.usmagazine.com/celebrity-news/pictures/two-and-a-half-mens-charlie-sheen-chuck-lorres-ups-and-downs/)



