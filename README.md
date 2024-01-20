# data-sourcing-challenge

![Final Dataframe Snapshot](/output/df_demo_image.jpg)

## Module 6 Challenge: Data Sourcing

In this project we utilized API keys from both The New York Times and The Movie Database to find movie reviews and then gather more information about each movie reviewed.

Main python notebook (retrieve_movie_data.ipynb) is in Repo main folder.

Final CSV is found at /Output/movie_data.csv.

A fun little project to work through! Building queries is a bit of a pain, but interesting to see how easy it is to get data from an API. Fingers crossed I did it all correctly!!!

## Work to be Done Outside of Prompt

### Remove Non-Informative Columns

The excersize prompts to drop the 'byline.person' column. This seems reasonable because it appears to contain duplicate information. Were I working with this data in real life, I'd consider also dropping the following columns as they contain no, non-null data.
- headline.content_kicker
- headline.name
- headline.seo
- headline.sub
- byline.organization

### Unify Date Columns

The dataframe contains two columns listing dates -- release_date and publication_date. The formatting is different for each. Conversation to a datetime object before exporting to csv would simply later processing.

## Bugs

### Movie Title Extraction

The prompted lambda extract movie title from 'headline.main' is not able to handle the format of all fields. It would take a little experiementation but it appears there could be a better way. First thought is looking for the single quote character (') instead of the word review.

### TMDB Request Speed Limit
When executed as instructed, the TMDB request counter only limits the script to fewer than 100 requests per second. This is because the script performs 2 requests every time the counter increments. Given that the API speed limit is 50 requests per second, this could pose a problem. Fortuantely, the block of code in question takes longer than 0.02s to run.