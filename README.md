# Scraping list of BBC's 100 greatest movies  of the 21st Century and the directors' info.

The aim of this project is to build a map showing the countries of origin and ratings of the different directors of movies rated in the BBC 21st Century's 100 greatest films mirrored here http://floatingmedia.com/columbia/BBC.html to preserve its original format.

Scraped the entire list of BBC's 21st Century’s 100 greatest films and used the list to scrape the IMDB page of each movie titles and their directors.

After first scraping the '100 greatest films' list, I outputted the result containing the movie critics' names, critics' organization, critics' countries of origin, movie names  and directors' names and year the movies were produced in `movie_data_copy.csv`.

In `scraping_director_data`, I scraped for individual url of each movie director's imdb page and then scrape the data for each name already identified in the `movie_data_copy` file to find the date of birth of each director and country of origin of each director.

I created another csv as `movie_data_merged` which contains this result, merged with the movie critics' names, critics' organization, critics' countries of origin, movie names  and directors' names and year the movies already identified in the initial dataframe.

I imported this merged dataframe into the `map_building` notebook and used pandas to do some basic analysis to first of all exclude all directors born in the US. The aim is to build a map that shows the countries of origin of all directors born outside the US and their ratings.

The analysis show directors with the highest number of counts(ratings) and with this, I built my html articles and headlines.

I imported a json file containing geometry data for each country and merged the articles and headlines I have created into this with an additional column for color.
The map is built with mapbox.
