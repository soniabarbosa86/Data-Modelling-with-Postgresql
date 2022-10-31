# <h1 align="center">Data Modeling with Postgres Project</h1>


## Table of contents
* [Introduction](#introduction)
* [Project Description](#project_description)
* [Datasets](#datasets)
* [Environment(s)](#environment)
* [Files](#Files)
* [Tables](#tables)
* [Process](#Process)




## Introduction
This project was part of my training for Udacity Program for Data Engineers. A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently this was not possible as all the information was stored in different directories of json logs.
The aim for this project was to create a PostGres database for the company to be able to query and analyze what type of songs their users are listening to. 


## Project Description
Define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

## Datasets
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID.

The second dataset consists of log files in JSON format based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.The log files in the dataset are partitioned by year and month.

## Environments
For this project we used Jupyter Lab and worked with python files as well as jupyter notebooks.

## Files
- **test.ipynb**  Displays the first few rows of each table to let you check your database
- **create_tables.py** drops and creates the tables. This file needs to be rerun each time before running the ETL scripts.
- **etl.ipynb** Reads and processes a single file from song_data and log_data and loads the data into the tables. This notebook contains detailed instructions on the ETL process for each of the tables.
- **etl.py** reads and processes files from song_data and log_data and loads them into the tables. 
- **sql_queries.py** Sql queries to drop and re-create table structures in the database sparkifydb.
- **README.md** Background and information on the project.


## Tables
As the aim for this project was to create a PostGres database for the company to be able to query and analyze what type of songs their users are listening to, the schema selected is a star schema. The fact tables contains the specific measurables or primary data to be analyzed and it was taken from the log data files:

- **songplay_id**, **start_time**, **user_id**, **level**, **song_id**, **artist_id**, **session_id, **location**, **user_agent**

The dimensions tables store supporting information to the fact table and contains a primary key that relates to the fact table.
- **users** - users of the application:
user_id, first_name, last_name, gender, level
- **songs** - songs in music database
song_id, title, artist_id, year, duration
- **artists** - artists in the database
artist_id, name, location, latitude, longitude
- **time** - timestamps of records in songplays broken down into specific units
start_time, hour, day, week, month, year, weekday

## Process

In order to complete the the the project the following steps were taken:

* 
* Develop an ETL process for each table and test to confirm that the records were inserted into the right tables
