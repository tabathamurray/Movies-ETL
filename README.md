# Detailed Instructions From Your Instructor Team

The objective of this challenge is for you to create an automated ETL pipeline using a function that takes in the three data files and performs the extraction, cleans and transforms the data using Pandas and regular expressions, and then loads the new data into PostgreSQL database.

## Deliverable 1: Write an ETL function to read three data files

For the first deliverable, we are asking you to write a function that reads in three files as arguments and converts the files to Pandas DataFrames. This deliverable shouldn't be too challenging. But it is important to get the data passed into the function to convert the JSON data and CSV files to DataFrames.

* We have provided [starter code](./Resources/ETL_Deliverable1_starter_code.ipynb) that you should download and add to your Movies-ETL GitHub folder, and rename the file `ETL_function_test.ipynb`. The starter code, has commented steps in the file where you will need to add the modified code from the module solution to complete this part of the challenge.

    * The code in Steps 6-11 is to help you read in the files and display the DataFrames. In Step 7, we have made the three variables equal to the function name.

    ``` python
    # 7. Set the three variables in Step 6 equal to the function created in Step 1.
    wiki_file, kaggle_file, ratings_file = function_name()
    ```

    * This allows you to change the variables by assignment. This is done in Step 8, where we assign the DataFrames equal to these variables in order to display the DataFrames.

    ``` python
    # 8. Set the DataFrames from the return statement equal to the file names in Step 6.
    wiki_movies_df = wiki_file
    kaggle_metadata = kaggle_file
    ratings = ratings_file

    ```

## Deliverable 2:  Extract and Transform the Wikipedia Data

For the second deliverable, you will need to extract, clean, and transform the Wikipedia data so it can be merged with the Kaggle metadata in Deliverable 3.

* This deliverable will be a bit challenging, there is a lot of code to add and modify so that the function works without errors. Be mindful of formatting. We encourage you to keep or edit the commented sections for an easier workflow.

* For this deliverable we have provided [starter code](./Resources/ETL_Deliverable2_starter_code.ipynb) that you should download and add to your Movies-ETL GitHub folder, and rename the file `ETL_clean_wiki_movies.ipynb`.

* In the `ETL_clean_wiki_movies.ipynb` file you can add the clean movie function from the module that takes in the argument, "movie" before the function you wrote in Deliverable 1, and then add the function that reads in the three data files in the next cell.

* There is one new task in this deliverable. In Step 6, you will need to write a `try-except` block that will catch errors while extracting the IMDb ID using a regular expression string and dropping any `imdb_id` duplicates. If there is an error, capture and print the exception. This will require you to refactor the code form the module.

The `wiki_movies_df` DataFrame should look like this:

![The ratings DataFrame.](./Resources/D2_wiki_movies_df.png)

The columns of `wiki_movies_df` DataFrame should look like this:

![The columns of the wiki_movies_df DataFrame.](./Resources/D2_wiki_movies_df_columns.png)

## Deliverable 3: Extract and Transform the Kaggle Data

For the third deliverable, you will need to extract, clean, and transform the Kaggle metadata and MovieLens rating data and then convert the transformed data into separate DataFrames. Then, you’ll merge the Kaggle metadata DataFrame with the Wikipedia movies DataFrame to create the `movies_df`. Finally, you’ll merge the MovieLens rating data DataFrame with the `movies_df` DataFrame to create the `movies_with_ratings_df`.

* This deliverable will be challenging. Again, there is a lot of code to add and modify so that the function works without errors, which can lead to errors. Be mindful of formatting. We encourage you to keep or edit the commented sections for an easier workflow.

* For this deliverable we have provided [starter code](./Resources/ETL_Deliverable3_starter_code.ipynb) that you should download and add to your Movies-ETL GitHub folder, and rename the file `ETL_clean_kaggle_data.ipynb`.

* In the `ETL_clean_kaggle_data.ipynb` file you can add the clean movie function in the second cell, and then add the function you wrote in Deliverable 1 that reads in the three data files in the third cell. you'll need to add all the code you wrote for Deliverable 2 above the following step,    `2. Clean the Kaggle metadata`.

The `movies_df` DataFrame should look like this:

![The ratings DataFrame.](./Resources/D3_movies_df.png)

The `movies_with_ratings_df` DataFrame should look like this:

![The columns of the wiki_movies_df DataFrame.](./Resources/D3_movies_ratings_df.png)

## Deliverable 4: Create the Movie Database

For the final deliverable, you will need to load the new data into PostgreSQL database.

* First, you'll need to copy the `ETL_clean_kaggle_data.ipynb` file in the Movies-ETL GitHub and rename the file `ETL_create_database.ipynb`.

* When you add the code to create the connection to the postgreSQL database that converts the `movies_df` DataFrame to a SQL database you'll neeed to use `'replace'` for the `if_exists` parameter so that the `movies_df` DataFrame isn't appended to the `movies` table.

* Before you add the MovieLens rating CSV data to the database, you'll need to drop the table in postgreSQL. This should be familiar to you as you have covered dropping tables in previous module.

## Submission

Make sure you upload the following to your Movies-ETL GitHub repository:

1. The `ETL_function_test.ipynb` file.
2. The `ETL_clean_wiki_movies.ipynb` file.
3. The `ETL_clean_kaggle_data.ipynb` file.
4. The `ETL_create_database.ipynb` file.
5. A Resources folder with the `wikipedia_movies.json`, `movies_metadata.csv`, `ratings.csv`, `movies_query.png`, and `ratings_query.png` files.
6. A README.md that describes the purpose of the repository.  Although there is no graded written analysis for this challenge, it is encouraged and good practice to add a brief description of your project.

## Grading Rubric

The [ETL-Movies Grading Rubric](./Resources/Module_8_Challenge_Grading_Rubric.pdf) is provided for you to use when grading you' submissions.
