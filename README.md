# Scraping list of BBC's 100 greatest movies  of the 21st Century and the directors' info.

The aim of this project is to build a map showing the countries of origin and ratings of the different directors of movies rated in the BBC 21st Century's 100 greatest films mirrored here http://floatingmedia.com/columbia/BBC.html to preserve its original format.

The scraping of the list starts from the notebook [BBC_project_code_steps(1)](https://github.com/kfalayi/Scraping-best-movies-directors-info/blob/main/BBC_project_code_steps(1).ipynb) using BeautifulSoup and Regex to identify specific patterns. This first scrape targets the names of the 177 critics who voted in the list,  the critics' organsation, critics' country, movie names, directors and year of movie release.

The result is saved in the CSV file `movie_data.csv`.
My next scrape in the [scraping_director_data.ipynb](https://github.com/kfalayi/Scraping-best-movies-directors-info/blob/main/scraping_director_data.ipynb) file is done using a copy of the movie_data file `movie_data_copy.csv` in order not to tamper with the original file in case I make changes to it along the way.

I imported pandas and numpy and cleaned up the columns a bit using regex and the string replace method. Then I imported BeautifulSoup which would be used to scrape to scrape the IMDB page of each movie titles and their directors already identified in `movie_data.csv`.

First I needed a sample of the url or the IMDB page of a director to see the structure and imported requests to get this url. With BeautifulSoup, I looped and parsed the html structurue of each director in my list to scrape the date of birth of each director and their country of origin. In looping through the names and urls, because of the likelihood that many of the names would not turn up the needed details, I used try and except to ensure my code doesn't break even when some names turn up no results.

Then I saved the result in the CSV file `director_data.csv`. I joined the movie_data dataframe to the director_data dataframe and saved the result in another CSV file `movie_data_mertged.csv` which contains this result, merged with the movie critics' names, critics' organization, critics' countries of origin, movie names  and directors' names and year the movies already identified in the initial dataframe.

I imported this merged dataframe into the `map_building` notebook and used pandas to do some basic analysis to first of all exclude all directors born in the US. The aim is to build a map that shows the countries of origin of all directors born outside the US and their ratings.

The analysis show directors with the highest number of counts(ratings) and with this, I built my html articles and headlines.

I imported a json file containing geometry data for each country and merged the articles and headlines I have created into this with an additional column for color.
The map is built with mapbox.
