# Data Modeling with Postgres
### Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

### Project Description
In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

### Achievements
Data modeling with PostgreSQL and building an ETL pipeline using Python. Define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in PostgreSQL using Python and SQL.
Skills include:
* Building out an ETL pipeline using Python
* Creating a database schema and ETL pipeline for this analysis
* Creating a PostgreSQL database with tables designed to optimize queries on song play analysis.

# Available Data
### Song Dataset
The first dataset is a subset of real data from the [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong). Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

```
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json
```
And below is an example of what a single song file, TRAABJL12903CDCF1A.json, looks like.
```
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```
### Log Dataset
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from a music streaming app based on specified configurations.

The log files in the dataset you'll be working with are partitioned by year and month. For example, here are filepaths to two files in this dataset.

```
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json
```

# Schema for Song Play Analysis
<img src="sparkifydb_erd.png" width="50%"/>

#### Fact Table
1. songplays - records in log data associated with song plays i.e. records with page `NextSong`
    * songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

#### Dimension Tables
2. <b>users</b> - users in the app
    * user_id, first_name, last_name, gender, level
3. <b>songs</b> - songs in music database
    * song_id, title, artist_id, year, duration
4. <b>artists</b> - artists in music database
    * artist_id, name, location, lattitude, longitude
5. <b>time</b> - timestamps of records in <b>songplays</b> broken down into specific units
    * start_time, hour, day, week, month, year, weekday
    
### Project Template
To get started with the project, go to the workspace on the next page, where you'll find the project template files. You can work on your project and submit your work through this workspace. Alternatively, you can download the project template files from the Resources folder if you'd like to develop your project locally.

In addition to the data files, the project workspace includes six files:

<b>test.ipynb</b> displays the first few rows of each table to let you check your database.
<b>create_tables.py</b> drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
<b>etl.ipynb</b> reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
<b>etl.py</b> reads and processes files from song_data and log_data and loads them into your tables. You can fill this out based on your work in the ETL notebook.
<b>sql_queries.py</b> contains all your sql queries, and is imported into the last three files above.
<b>README.md</b> provides discussion on your project.