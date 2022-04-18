# Movies-ETL
## Overview
  An analysis was performed on movie rental data to determine which lower-budget movies would become popular to rent. The purpose was to provide the company with clean data sets from two data sources and to load them into an SQL database. The process needed to be automated so that it takes in new data, performs the appropriate transformations to clean the data, and then loads the tables into the database.   
## Results
### Read Three Data Files
  I created a function that takes in three data arguments (Wikipedia, Kaggle, and MovieLens) and reads them as Pandas DataFrames. This function then returned the three different DataFrames as wiki_movies_df, kaggle_metadata, and ratings. 
### Extract and Transform Wikipedia Data
  I then created a clean movies function that takes in one argument and cleans the data that was entered. This function combines alternative titles into one single list, and merges and changes the column names. I then reused the function from the above section to read in our data as DataFrames. I then called in the clean movies function to clean the DataFrames that were created. I then removed the columns where more than 90% of the data are null values and wrote a new function that uses RedEx expressions to rewrite the budget and box office data so it was all written in the same format. Lastly, I converted the release date column to datetime and the running time column into the same written format. The final Wiki Dataframe can be seen below:
 
 ![This is an image](https://github.com/dsilvaggio/Movies-ETL/blob/main/Resources/Screen%20Shot%202022-04-17%20at%206.51.54%20PM.png)

### Extract and Transform Kaggle Data
  To clean the Kaggle Data, I resued all of the functions that I had written above to clean the Wikipedia Data. I added lines of code in my clean movie function that cleaned the Kaggle data by fixing column data types. I then merged the Kaggle Data with the Wiki Data into a new data frame, filled in any missing data, and dropped repeating columns. I filtered the DataFrame for specific columns and renamed them to be more consistent. This DataFrame can be seen below:
  
  ![This is an image](https://github.com/dsilvaggio/Movies-ETL/blob/main/Resources/Screen%20Shot%202022-04-17%20at%207.04.12%20PM.png)
  
  Lastly, I grouped the rating data to get the rating counts for each Movie Id and merged this with the above DataFrame into a new DataFrame. This final DataFrame is below:
  
  ![This is an image](https://github.com/dsilvaggio/Movies-ETL/blob/main/Resources/Screen%20Shot%202022-04-17%20at%207.05.52%20PM.png)
### Create a Movie Database
  The final step was to upload these DataFrames into a SQL Database. I created a Movies_Data database in SQL and connected with Pandas using SQLAlchemy. I saved the movies_df DataFrame to a SQL table named "movies" and the rating data to a SQL table named "ratings". To check that they were both imported correctly, I queried the tables using SQL to check the row count. The counts for each table are below:
  
  ![This is an image](https://github.com/dsilvaggio/Movies-ETL/blob/main/Resources/movies_query.png)
  
  ![This is an image](https://github.com/dsilvaggio/Movies-ETL/blob/main/Resources/ratings_query.png)
