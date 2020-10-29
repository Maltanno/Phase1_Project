# FlatIron School Phase 1 Project:  
## Insights for a new movie studio

Tasked to:
- Analyse data from the movie industry
- Explore what goes into making a successful movie
- Provide actionable insights

## Questions asked:
1. How has the popularity of different genres changed over time?
    - In which genre should we make a movie?
2. Which two people give the most return when working together?

## Recommendations:
1.
- I recommend making a Fantasy-Adventure movie. These genres have shown to be consistently popular. Release is favoured towards summer, of an even year.

- If you want to go high-risk - high-reward, you could try History, War or Western; to make a film that stands out in its genre.

- Whereas if you were looking to garner renown even at the expense of audience size, then you'd want to make documentaries.
   
   
2.
Filmmakers who make the highest RoI are:
- Steven Schneider, Oren Peli, Jason Blum;
- Michael Bay, Andrew Form, Brad Fuller;   

On one hand the first trio have a higher 30th percentile; on the other, the second trio have worked together on more films and so are less of a gamble. Both sets are predominantly in the horror sphere.

If you want something a bit more family friendly there's:
- Janet Healy & Christopher Meledandri


## Data
Used the provided datasets in the folder: zippedData  
Data needed some cleaning, performed in the Cleaning-MA notebook

## Question 1

### Data Used
Dataset: The Movie DataBase
- For reliable vote scores: Only considering films with 5 or more votes
- Only looking at films ~2010-2019
     -This is still almost 13k films

### Data Engineering
For seeing how the popularity changes over time I used the data provided to create time series data: a rolling average with a 6 month window, finding aggregates for a data point every 3 months.

### Visualisations
I could then create graphs with a different line for each selected genre for a variety of aggregates over time:
![Num_films](https://github.com/Maltanno/Phase1_Project/blob/MAwip/vis_slides/num_films.jpg)
![Median](https://github.com/Maltanno/Phase1_Project/blob/MAwip/vis_slides/median-1.jpg)
![Weighted_sum](https://github.com/Maltanno/Phase1_Project/blob/MAwip/vis_slides/weighted_sum-1.jpg)
![Western](https://github.com/Maltanno/Phase1_Project/blob/MAwip/vis_slides/western-1.jpg)
![Weighted_mean](https://github.com/Maltanno/Phase1_Project/blob/MAwip/vis_slides/weighted_mean-1.jpg)

### Recommendation
Making a Fantasy-Adventure movie due to those genres' consistent Popularity

## Question 2

### Data Used
imdb.principles -to find people who work together
imdb.basics -merge by tconst(the film code); to find the primary title
tn.movie_budgets -join by title; use budget and wwgross to find RoI
imdb.names -join by name code (nconst) to find names

### Data Engineering
- Join datasets together, calculate RoI
- Create a dictionary with the pairs of name-codes as keys, and a list of their joint film-codes as values
- Make a dataframe from this, replace film-codes with RoI
- find 30th percentile of RoI for each pair
- Make the dataframe again but this time replace film-codes with Titles
- Join these two dataframes together
- Add names from the name codes
- Look at the top 100, pick by hand those to drop for only being in franchises together

### Visualisations
![Pairs](https://github.com/Maltanno/Phase1_Project/blob/MAwip/figs/pairs_fig.png)

### Recommendation
Pairs or, as found, trios who make the highest RoI are:
- Steven Schneider, Oren Peli, Jason Blum;
- Michael Bay, Andrew Form, Brad Fuller;
Or for something more family friendly
- Janet Healy & Christopher Meledandri







