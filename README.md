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
