# Box Office Analysis

**Authors**: James Meredith, Jonathan Brown, Samuel Song

Please review our full analysis in our Jupyter Notebooks, [Data Cleaning here,](./code/data_cleaning.ipynb) [Exploratory Data Analysis (EDA) here](./code/eda_notebook.ipynb),and [our presentation slides](./presentation.pdf).

## Overview

Our company has decided to enter the movie studio space, but they need help figuring out what type of movies to create. The purpose of this data analysis project is to explore what types of films are doing the best at the box office in order to translate those findings into actionable insights that the head of our company's new movie studio can use to help decide what type of films to create.

## Data

We have used data from [The Box Office Mojo](https://www.boxofficemojo.com), [Rotten Tomatoes](https://www.rottentomatoes.com), [The Numbers Database](https://www.the-numbers.com), [IMDB](https://www.imdb.com), and [The Movie Database](https://www.themoviedb.org)

Our analysis began by understanding and cleaning the datasets provided. Different types of information were scattered throughout each dataset. So it was important for us to understand what information came from which dataset:
- IMDB:
    - Base movie info
    - Run Time
    - AKA's (used to separate by regon, want US based only)
    - Directors
- The Numbers DB (TNDB)
    - Budgets
    - Worldwide Profits
- Box Office Mojo (BOM)
    - Worldwide gross
- Rotten Tomatoes
    - Movie Ratings (R, PG-13, PG, etc)
    - Approval Ratings
<br>
We opted out of using The Movie Database(TMDB) because it had only information based on popularity on their website. We found this to be too abstract and a biased representation of movie-goers. 
<br>

## Methods
To help guide our exploration, we brainstormed several ideas for interesting comparisons and explored each one in our [EDA notebook](./code/eda_notebook.ipynb):
* Genre vs Rating
* Genre vs Gross
* Genre vs Budget
* Budget vs Gross
* Writer vs Gross
* Director vs Gross
* Movie Rating (R, PG-13, PG, etc) vs Approval Ratings
* Runtime vs Gross
* Runtime vs Budget
* Approval Rating vs Gross

By using IMDB as the main database, we merged together the financial data points from the Box Office Mojo and The Numbers datasets to the IMDB dataset by movie title to get a list of movies to analyze. This list is what was used to get the top average grossing directors, a list of movies with a net profit/net loss, and runtime vs worldwide gross. 

<br>
The roadblocks we encountered were mostly in the cleaning process and dealt with an incomplete database. 
- Avatar was being shown as a Japanese horror film
- Titanic was also being shown as a Japanese film
    - Appeared that James Cameron's earlier films (pre Avatar-2) were not in the IMDB database, so merging the financials dataset to IMDB had put together James Cameron's films onto different directors of the same movie name
    - This was remedied by selecting US based movies/directors only. Ultimately this had Titanic and Avatar not selected at all in the final table. 
    - It then became apparent that the databases being used were quite incomplete
- Multiple genres were listed in a single column. So intial .groupby() methods had yieled anywhere from a single genre to a cluster of three genres.
    - This did not give us a clear picture of genre distribution
    - Remedied by creating separate columns
    - **JAMES FILL IN HERE HOW IT WAS DONE**

<br>

After exploring each category, we decided that the four categories we wanted to focus on for our presentation were:
- Budget
- Runtime
- Genres
- Directors

## Results

We started the project by looking at the top grossing movies overall from google. The list mostly comprised of action/animation films, so we intuitively believed action/animation would do the best.
<br>
Results of the analysis revealed our intuition was mostly correct. Action/Animation were among the top grossing films, and many top directors were animators or action movie directors. 

### Visualization of Budget vs Profit

<br>
Budgeting: It was found that having a low budget of $0 to $16 million had only a 48% success rate of having a positive profit. Mid budgets from $16 to $77.5 million had about a 65% success rate, and high budgets above $77.5 million had an 88.6% success rate. It's almost like gambling because spending less has a higher rate of failing. Spending more has a higher rate of success, BUT it is not guaranteed success. One can have high confidence in the film if opting for a high budget film. 
- After some research, there was no concrete answer for what is considered low, mid, high budget films (many different answers were found)
- These numbers for budgeting came from some statistical calculations
- The frequency of the data was extremely skewed right
- Median was only $16m while mean was $32m and standard deviation was $45m!
- One standard deviation to the left yieled a negative budget, which makes no sense
- It was decided to use the median as the cutoff for low budgets, as it may reflect real life standards. More low end budget films should exist.

### Visualization of Runtime vs Average Worldwide Gross

<br>
Runtime: According to [this article,](https://stephenfollows.com/are-hollywood-movies-getting-longer/#:~:text=Length%20of%20Hollywood%20movies&text=Half%20of%20all%20Hollywood%20movies,shortest%20are%20animations%20and%20documentaries.) half of Hollywood films are between 96 and 120 minutes long. Using this as a category indicator for runtime, we looked at the average worldwide gross for movies over 120 minutes, 96 minutes to 120 minutes, and below 96 minutes. Movies over 120 minutes, or 2 hours, have the superior average gross in millions.

### Visualiation of Genre vs Average Worldwide Gross

<br>
Genre: The top three grossing genres were Action, Animation, and Science Fiction.

### Visualization of Top Director vs Average Net Profit


## Conclusions

Based on the analysis of the authors:
- Budget: High end budget films are a heavy investment, but tend to succeed more.
    - Low budget films tend to net a loss profit but are a low investment compared to other budgets.
    - Mid budget films have little more than a 50% chance of being successful for a more hefty 'buy in'.
    - Ultimately this is personally up to the studio
- Runtime: A runtime of 2 hours or more is shown to have higher gross than movies less than 2 hours.
    - This may be influenced by budget. More runtime = more budget.
- Genres: Action, Animation, and Science Fiction have proven to be solid genre choices to make films.
- Directors: The top net profit directors were mostly comprised of animation or action directors. This may also supplement the above claim of animated/action being the superior genre choice.

### Next Steps

- Further look into budgets of animated movies vs live action movies.
    - Maybe voice actors cost less than live action actors.
    - Maybe there's a better ROI for animated movies vs live action movies.
- Look into directors according to genre in order to give the best director recommendation.
- Look into the how movie runtimes have changed over time.
- See how profitable genres have been over time.

## For More Information

Please review our full analysis in our Jupyter Notebooks, [Data Cleaning here,](./code/data_cleaning.ipynb) [Exploratory Data Analysis (EDA) here](./code/eda_notebook.ipynb),and [our presentation slides](./presentation.pdf).

For any additional questions, please contact James Meredith at jam637.jlm@gmail.com, Jonathan Brown at jonnie.brown4@gmail.com and Samuel Song at samueld.song@gmail.com

## Repository Structure

```
├── code
│   ├── __init__.py
│   ├── visualizations.py
│   ├── data_preparation.py
│   └── eda_notebook.ipynb
├── data
├── images
├── __init__.py
├── README.md
├── box-office-analysis.ipynb
└── presentation.pdf

```
