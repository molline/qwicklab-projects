#LAB: GCP Fundamentals: Getting Started with BigQuery

##Objectives

In this lab we will learn how to perform the following tasks
	-Load data from Cloud Storage into BigWuery
	-Perform a query on the data in BigQuery

##Steps:

1.	Loading data from Cloud Storage into BigQuery
	
	bq --location=europewest1 mk --dataset logdata

	bq load --autodetect --source_format=CSV logdata.accesslog gs://cloud-training/gcpfci/access_log.csv

	bq ls -j [project_id]

	bq head [project_id]:logdata.accesslog

2. Perform a query on data using the bq wweb UI
	bq query "select int64_field_6 as hour, count(*) as hitcount from logdata.accesslog group by hour order by hour"




3. Perform a query on the data using the bq command

	bq query "select string_field_10 as request, count(*) as requestcount from logdata.accesslog group by request order by requestcount desc" 


