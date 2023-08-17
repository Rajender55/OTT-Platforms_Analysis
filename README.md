# OTT-Platforms_Analysis
Design and implement end-to-end ETL data ingestion pipelines for migrating OTT platform data to Azure Cloud, followed by batch and interactive analysis in DataBricks.

***********************************
Goals:
•	Develop end-to-end ETL pipelines, seamlessly transferring Over-the-top (OTT) platform data to Azure Cloud
•	Comprehensive analysis through batch, interactive processes using Data bricks.
•	Engineer a robust recommendation system for enhancing user engagement and profitability on the OTT platform by delivering personalized content suggestions to users.
***********************************
Configuration of the cluster:
4 node, 8 cores/Node, 32 GB RAM/Node
4 GB RAM/core
1 executor- - - - -1 core
Time executor principle- - - - - 
***********************************
Data description:
Amazon_prime.csv: 
    (Movie_Name, Language, Rating, Runtime, Year, Age_rating, Review)
Number of Rows : 8127
Netflix.csv: 
(Show_id, type, title, Director, Cast, Country, Date_added, Year, Age_rating, Duration, Listed_in, Description)
Number of Rows : 8808
Disney_plus.csv:
(Imdb_id, title, plot, type, age_rating, year, released_at, added_at, runtime, genre, Director, Writer, Actors, Language, Country, Awards, Metascore, Imdb_rating, imdb_votes)
Number of Rows :   895
***********************************
Explanation of architectures: 
1.Spark architecture
Source data is in Azure SQL DB. We have a scheduled pipeline for bringing the data ffrom source to ADLS storage system in Azure
Analyzing the data in Databricks after mounting the databricks platform with ADLS
-if the org wants real time analysis and visualization then databricks can be distectly coupled with power BI
---if org needs the analysed or cleaned in a central repository system, then we can store the data azure synapse warehouse and we can connect powerBI with synapse
Analysis:
Mounting the databricks with ADLS
Cleaning the data: 
Handling the data types, 
different column values according to the requirement,
Handling the Null values (we the ‘’unknown”, mean values from the genres, director names
Handling the date time values---to the required format
Exploding the rows according to the requirement,
It will increase the processing time>>now we have to go for the optimization techniques
Increasing the number of partitions, number of executors
RDD----cryo serializer, repartitioning, checking the performance on the query execution in spark 

2.Hadoop architecture:
HDInsight----PAAS in Azure---we have i
1.The source data in azure SQL db, implementing the sqoop pipeline to bring the data to Hive datawarehouse
2.Analyzing the data using Hive
3.Used optimization techniques partitioning and bucketing, file formatting to improve the performance of the queries  
3.Exporting the all the results to Azure SQL Db using Sqoop
4.Connecting Azure SQL DB with Power BI
***********************************
Visualization:
Creating the interactive dashboards for the subscribers in OTT platforms
