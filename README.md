# Charlie's Gone, But the Show Went On: A Data-Driven Analysis of the Kutcher Transition in "Two and a Half Men

![photo](/assets/img/Two-and-a-Half-Men.jpg) 
Warner Bros Tv/Chuck Lorre Prod/Kobal/Shutterstock

#### Two and a Half Men" was a wildly popular CBS sitcom that followed the life of Charlie Harper (Charlie Sheen), a carefree bachelor whose lifestyle is disrupted when his divorced brother Alan (Jon Cryer) and nephew Jake (Angus T. Jones) move in with him. The show became a cultural phenomenon, running for 12 seasons from 2003 to 2015.
#### The series faced an unprecedented challenge in 2011 when Charlie Sheen was dismissed following public controversies. Ashton Kutcher joined as a new lead character, creating a natural experiment in television - how does replacing a lead actor impact a show's success? This project employs data science and machine learning techniques to quantify that impact.

## Data Collection and Preparation
Since no ready-to-use datasets were available, I conducted primary research by gathering data from IMDb, which contained episode ratings and user reviews. Using the Selenium library, I scraped two key components from the website:
#### 1. Episode ratings: Each entry includes the episode title, episode description, season and episode number, average rating, vote count, and air date. 
#### 2. User reviews: Unstructured textual feedback containing review title, review text, rating (if provided), and date posted. 
The raw scraped data was cleaned and formatted into structured CSVs, ensuring consistency for further statistical and textual analysis.

## IMDB ratings over the show
![Average ratings by season](/assets/img/avg-ratings-by-season.png) 

The show maintained consistently strong ratings above 7.5 during Charlie Sheen's eight-season tenure. Following his departure and Ashton Kutcher's arrival in Season 9, ratings fell to 6.0, with a temporary rebound before ultimately declining to 5.4 in the final season. This rating pattern coincided with the lead actor transition, showing a notable shift in audience reception during the later seasons.

![Average ratings by season](/assets/img/avg-ratings-by-season.png) 

The episode ratings show distinct patterns between the two eras. Sheen's performances ranged from a season-low 7.1 (Episode 5) to a peak of 8.2 in his final season. Kutcher's episodes opened at a series-low 5.75 (Episode 5) before recovering to 6.73 (Episode 19), still significantly below Sheen's average performance. The data reveals a notable rating differential between the two leads' tenures.

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

The analysis of review word clouds reveals distinct patterns in viewer sentiment. In neutral reviews, prominent terms like "bring back," "without," "left," and "ruined" frequently appear, potentially reflecting audience reactions to the cast transition. Meanwhile, positive reviews show "Charlie" as the most dominant word, suggesting his strong association with favorable viewer perceptions during his tenure on the show.

## Decision Tree Regressor

Decision trees can effectively predict numbers like TV ratings by finding patterns in data. The model works by repeatedly splitting the data into groups based on important factors.

For this project, I built a decision tree to guess episode ratings. First, I removed:

Actual ratings (prevent bias)

Text lengths (low relevance)


![Result](/assets/img/decision-tree-result.png) 

The model performed well at guessing ratings. The below image shows how the predicted points are close to the line which represents the actual values. While these results look good, I'll test other methods to find the best approach.

![Actual vs Predicted](/assets/img/actual-vs-predicted.png) 

## Random Forest vs. XGBoost: Which Did Better?

Random Forest and XGBoost are both powerful ensemble methods that combine multiple decision trees to improve predictions. Random Forest builds independent trees and averages their results, while XGBoost sequentially improves trees by learning from previous errors.

![Actual vs Predicted](/assets/img/rf-vs-xgb.png) 

In our tests, Random Forest captured slightly better overall trends (R² 0.9039 vs 0.8999), while XGBoost delivered marginally more precise individual predictions (MAE 0.1982 vs 0.2038). The choice depends on whether you prioritize broad pattern recognition or exact rating estimates.

![Feature importance](/assets/img/feature-importance.png) 


the figure above explains season and cast changes (like Charlie Sheen's presence) are the biggest rating predictors. While vote counts have some influence, episode numbers contribute little - we might remove this feature to boost accuracy, but we have to proceed carefully to avoid overfitting the model to our specific dataset.

## Sentiment Classifier

To analyze viewer sentiment, I developed a classification system comparing four machine learning approaches:

Logistic Regression - A linear model estimating positive/negative probability

Naive Bayes - Applies probability theory with feature independence assumption

SVM (Support Vector Machine) - Creates optimal decision boundaries in high-dimensional space

Neural Network - Deep learning model detecting complex sentiment patterns

![Sentiment classifier result](/assets/img/sentiment-classifier-results.png) 


The evaluation shows logistic regression performs best overall with 83% accuracy and strong F1 scores for neutral (0.87) and positive (0.83) sentiments. While Naive Bayes handles negative reviews slightly better (F1=0.71) and SVM excels at neutral recall (96%), all models struggle with negative sentiment detection (30-60% recall).

![confusion matrix](/assets/img/confusion-matrix.png) 

Logistic regression emerges as the preferred default choice, with potential adjustments to class weighting for improved negative detection. The consistent challenges with negative sentiment classification across models may indicate underlying dataset limitations.
