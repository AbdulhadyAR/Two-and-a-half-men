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
![Average rating by season](/assets/img/avg-rating-by-season.png) 
The show thrived with Charlie Sheen, maintaining strong ratings above 7.5 for eight seasons. His departure marked a turning point - when Ashton Kutcher took over in Season 9, ratings immediately dropped to 6.0. Though they saw a slight rebound afterward, the decline continued, bottoming out at 5.4 in the final season. This trajectory clearly demonstrates how crucial Sheen's presence was to the show's success and how difficult it proved to maintain audience engagement after such a significant cast change. The numbers tell a story of a series that never fully recovered from losing its original star.
