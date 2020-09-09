#Course: Google Cloud Platform Big Data and Machine Learning Fundamentals

#MODULE: Introduction to Google Cloud Platform

#LAB: Explore a BigQuery Public dataset


##Objectives

In this lab we will
	-Query a public dataset
	-Create a custom table 
	- Load data into a table
	-Query a table
##Steps:

1. 	Query a public dataset

	-Click ADD DATA > Explore public datasets

	-Search USA Names and view dataset

	-Query the dataset using bq commnand 

	bq query "SELECT name, gender, SUM(number) AS total FROM `bigquery-public-data.usa_names.usa_1910_2013` GROUP BY name, gender ORDER BY total DESC LIMIT 10"

2.	Create a custom Table
 
	- Download the baby names zip file unzip it and note the location of yob2014.txt

	-create a dataset

		bq --location=US mk babynames

3. Load data into a new table
	
	-Upload the yob2014.txt file using the upload file option in the more dropdown

	-Load the data to a table names_2014 (replace the "[project_ID]" with your project_ID)

	bq load \
	--source_format=CSV \
	 [project_ID]:babynames.names_2014 \
	  ./yob2014.txt \
	name:STRING,gender:STRING,count:INTEGER

4.	Query the table
	
	 bq query "select name, count from babynames.names_2014 where gender='M' order by count desc limit 5"

