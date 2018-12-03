# **_Movalyst_ from _Tools Project_ in Section 1**

## What is it?
_Movalyst_ is a powerful movie data analyzing tool based on data from Box Office Mojo and Rotten Tomatoes. With Movalyst, it is easy to scrape movies data, display tables and visualized graphs. Users can find data for top 100 movies every year from 1980 until now and check data-based analysis result. 

## What we do?
Before analyzing data, we first create functions to scrape data from website. Movie data in one specific year can be found with these functions.
With data found in the preceding part, users can do further analyses including feature distribution, finding good actors,directors and attach showtime to movies etc.
We scrape reviews of top 30 movies in 2018 from Rotten Tomatoes to do text mining.
We conduct three types of sentiment analysis to reviews and recommend movies based on results.
We conduct topic modelling to all reviews and plot the pyLDAvis graph.
We use decision tree model to fit movies feature variables and identify the model by drawing ROC curve.

## Run instructions:
Here, you can find more details about Movalyst functions in a logical order and how to call the function in a right way:

- `movie_from_year(year)`: With this function, you can find a list of url of top 100 movies in the specified year and the names of them in a list. You need to input a year no earlier than 1980 and no later than this year as a parameter.
- `find_from_to(yearx,yeary)`: If you want to see top 100 movies from one year to the other, user this function. You just need to input a start year and an end year, you can get a dictionary with movie names as keys and movie urls as values.
- `gross_movie(name,begin_year,end_year)`: You could get a detailed table for a specific movie’s daily gross. The table contains day, rank, gross box office at that day, daily percentage change and weekly percentage change, etc.
-`data_movie(name,begin_year=1980,end_year=2018)`: With this function, you could get a specific movie's basic information including name, genre, runtime, budget, actors, directors and gross box office, etc.
- `data_movies_table(begin_year=1980,end_year=2018,input_name=None)`: With this function, you could get all movie's basic information including name, genre, runtime, budget, actors, directors and gross box office, etc.
- `movie_data_group(year)`: With this function, you can get some basic feature data of top 100 movies in a table with the specified year as you input. The features include Movie Name,Domestic Total Gross,Distributor,Release Time,Genre,Runtime,MPAA Rating,Production Budget,Worldwide Gross. This function is faster than data_movie_table but it has fewer features.
- `data_movies_format_01(begin_year=1980,end_year=2018,input_name=None)`: With this function, data of both domestic and foreign gross box office is cleaned and changed into int type data.
- `news_of_movie(name, year)`: With a name and the release year of that movie, you can get some news, however, this one is not so accurate, sometimes you get some news not relevant.
- `distributor_movie(name,year)`: If you want to know something about the data a specific distributor release within a specific year. You call this function with the distributor’s name and the year as inputs. You will get the movies’ grosses and opening time.
- `single_movie_gross_plot(name)`: With this function, you could get a line chart showing a movie's day-to-date change of its box office.
- `single_movie_dailychange_plot(name)`: With this function, you could get a line chart plotting a movie's daily-gross-percent-change.
- `domestic_foreign_dis(year)`: While some movies are focused in domestic markets, others are more targeted at the global market. To get this feature of the movie, simply play with this function which would present you with the ratio of domestic and foreign gross box office to the total gross box office, the movies with the 10 and 100 highest ratios and draw a pie chart accordingly.
- `market_data(year)`: Input a specific year, you can get a pie graph showing you the top 5 market capturing distributors with this function.
- `pie_graph(data,feature)`: With known data input as pandas dataframe, you can get a pie graph with top 5 proportion classes in a specific feature from the data input.
- `groupbybox(begin_year,end_year)`: With this function, movies are grouped by box office and divided into three categories according to their percentiles in the domestic box office as High, Notbad and Low.
- `showtimes(begin_year,end_year)`: Generally speaking, movie showtimes in North America is divided into five periods, which are spring, summer, fall, winter and holiday season. With this function, you would get a new column in the dataframe specifying the showtime that a movie falls in. This is an prerequisite for looking further into genres.
- `showtimestable(begin_year,end_year)`: This function presents you with a table showing the number and percentage of movies in each catogory under different box office level.
- `showtimeschart(begin_year,end_year)`: You are presented with two charts, respectively indicating the distribution of showtimes under the three box office catogories, and the distribution of box office under each showtime from begin_year to end_year.
- `genre(begin_year,end_year)`: A movie may fall into several genres at the same time. With this function, we split the genre and make it more clear for looking further into movie showtimes.
- `genretable(begin_year,end_year)`: This function presents you with a table showing the number and percentage of movies in each genre under different box office level.
- `genrechart(begin_year,end_year)`: You are presented with two charts, respectively indicating the distribution of genres under the three box office catogories, and the distribution of box office under each showtime from begin_year to end_year.
- `movie_trend(data,start_year,feature, list_of_feature)`:This function needs to be carried out after you get top 100 movie data for a consecutive periods of years. Then you input this data as the first parameter, input the start year of your data and a list of genres you want to see their trends, then this function will return you a line graph, showing you the trends of different classes in the feature you specify.
- `valuable_actors(year1,year2,top=5)`: With this function, a form is presented showing the actors involved in movies of 5 highest box office within the time period from year1 to year2.
- `valuable_directors(year1,year2,top=5)`: This is similar to the last function. With this function, you would find the most valuable movie directors from year1 to year2.
- `find_hit(year,rank)`: This is a function helping you to pin movie having small budgets but earning big grosses. You need to specify a year and a rank, for example, you want to see top 10 movies which earns a lot with little spending in 2018, you call find_hit(2018, 10).
- `get_review(name, page_length = 2, num = 20)`: Get a selected number of reviews based on movies name.
- `get_name_review(year, num = 30, page_length = 2, length = 20)`: Return a list with pairs of movie name and review. Here we only choose 20 reviews for each of top 30 movies.
- `get_pos_neg_words()`: Get positive and negative words from sentiment analysis lexicon.
- `do_pos_neg_sentiment_analysis(reviews)`: Get the proportion of positive and negative words in each review and return them in a table. 
- `get_nrc_data()`: Get an emotion dictionary based on NRC data.
- `comparative_emotion_analyzer(reviews,object_name="name")`: Identified the emotion corresponded by each word in the review and return a table with the weight of emotion for each movie. 
- `vader_comparison(reviews)`: Do vader analysis to reviews and return a table sorted by compound sentiment. 
- `get_recommendation(num)`: Assigned scores to movies in each method and give recommendation based on their total scores. Customers can input the number of recommendations they want.
- `remove_words(text_string,DELETE_WORDS=DELETE_WORDS) & remove_short_words(text_string,min_length = MIN_LENGTH)`:  Prepare text to be used in wordcloud by removing redundant and short words.
- `get_topics(num_topics = 5, passes = 10, num_words = 8)`: Get topics of all reviews with LDA model and draw pyLDAvis plot. Customers can choose the number of topics to generate.
- `get_decision_tree_table(year = 2018)`: Get movies data in recent three years, quantify movies’ feature variables and fit them with classification decision tree. The worldwide gross is set to be independent variable and classified based on third quatile value.

## Installation instructions:
In order to call functions of Movalyst, our users need to install the following modules from pypi:
- `!pip install requests --upgrade`
- `!pip install bs4 --upgrade`
- `!pip install datetime --upgrade`
- `!pip install pandas --upgrade`
- `!pip install matplotlib --upgrade`
- `!pip install nltk`
- `!pip install wordcloud`
- `!pip install vaderSentiment`
- `!pip install gensim`
- `!pip install pprint`
- `!pip install google-compute-engine`
- `!pip install pyLDAvis`
- `!pip install sklearn`
