# Open Movie Database and TasteDive Mashup API Project

## Project Overview
In this project, I'm going to take you through the process of creating movie recommendations by merging data from two different APIs. The TasteDive API allows us to input a movie (or bands, TV shows, etc.) and get a set of related items in return. On the other hand, the OMDB API allows us to input a movie title and receive detailed data about the movie, including scores from various review sites like Rotten Tomatoes and IMDB.

I'll be combining these two APIs to achieve our goal. Using TasteDive, I'll gather related movies for a list of titles. Then, I'll merge these lists of related movies and sort them based on their Rotten Tomatoes scores. This sorting will require making API calls to the OMDB API.

To ensure we don't run into problems with rate limits or site accessibility, there's a cache file available with results for all the queries I need to make to both OMDB and TasteDive. I'll be using `requests_with_caching.get()` instead of `requests.get()` to access this cache. If I encounter any issues, it could be due to improper query formatting or requesting data that doesn't exist in the cache. 

First, I'll start by fetching data from TasteDive. I'll define a function called `get_movies_from_tastedive`, which will take a string input representing a movie or music artist and return the 5 TasteDive results associated with that input. I'll make sure to get only movies and not other types of media. The result will be a Python dictionary with a single key, 'Similar'. This will be my initial step.

Next, I'll write a function called `extract_movie_titles` to extract just the list of movie titles from a dictionary returned by `get_movies_from_tastedive`. This will help me organize the data better.

Moving forward, I'll create a function named `get_related_titles`. It will accept a list of movie titles as input, get five related movies for each from TasteDive, extract their titles, and combine them into a single list.

For the OMDB part of the project, I'll define a function called `get_movie_data`. It will take a string parameter representing the title of a movie to search for and return a dictionary with information about that movie. I'll use `requests_with_caching.get()` again, ensuring that I provide the required keys 't' and 'r'.

I'll also create a function named `get_movie_rating` to extract the Rotten Tomatoes rating as an integer from an OMDB dictionary result for a specific movie. If there's no Rotten Tomatoes rating, it will return 0.

Finally, I'll define a function called `get_sorted_recommendations`, which will take a list of movie titles as input and return a sorted list of related movie titles, up to five for each input title. The sorting will be done in descending order by their Rotten Tomatoes rating, as determined by the `get_movie_rating` function. In case of ties, I'll break them in reverse alphabetic order.

This project will involve quite a bit of data manipulation and merging, but I'm excited to put it all together and create some fantastic movie recommendations!

## Project Description

The project comprises several key components:

1. **API Integration**: The project involves integrating the OMDb API to access movie data and the TasteDive API to access music recommendations.

2. **Movie Search and Details**: Users can search for movies by title, retrieve movie details, such as cast, plot, and ratings, and get recommendations for similar movies.

3. **Music Recommendations**: Users can explore music recommendations based on their movie interests. These recommendations could include soundtracks, artist suggestions, or music that complements the movie's theme.

4. **User Interface**: The project includes a user-friendly interface where users can interact with the application. It may be a web application or a command-line tool, depending on the implementation.

5. **Documentation**: The project documentation, including this README.md file, provides details on the project, its components, and how to use it.

## Contributors

- [Niraj Bansal](https://github.com/NirajB1602)

Feel free to fork, contribute, and share this project with others interested in creating a movie and music recommendation service through API mashups.

---

**Note:** The tasteDive API is no longer functional, however, it still works within the Runestone environment through the "requests_with_caching.get()" function.
