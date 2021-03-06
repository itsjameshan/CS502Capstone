# Team 3 Capstone: Real-Time Moive Rating Data Pipeline

Introduction
------------

This data pipline will process the Netflix moive real-time rating data, visualize the movie rating trend, and provide a scalable distributed database for real-time query.

Team member
------------

	Tongzhou Zhou, Bin Shi, Albert, Anthony

[Dataset](https://www.kaggle.com/netflix-inc/netflix-prize-data)
------------

	Netflix Prize data

Architecture
------------

	data-ingestion-sinking-layer: Kafka, Kafka Connect
	data-transformation-layer: Kafka Streaming
	data-storage-layer: AWS S3, Cassandra
	data-visualization-layer: NodeJS
	data-batch-processing-layer: Spark
	cloud-infrastructure: AWS

![img](https://s3-us-west-2.amazonaws.com/github-photo-links/Screen+Shot+2018-01-19+at+10.36.51+PM.png)
​	
​	
Detailed Schema
---------------

	Cassandra tables:

	CREATE TABLE movie_rating_cs502 (
			start_time timestamp,
			rating float,
			movie_id int,
			count int,
			movie_title text,
			PRIMARY KEY (start_time, rating, movie_id)
	) WITH CLUSTERING ORDER BY (rating DESC, movie_id ASC)
	
	CREATE TABLE bittiger.movie_cs502 (
			movie_id int,
			start_time timestamp,
			count int,
			movie_title text,
			rating float,
			PRIMARY KEY (movie_id, start_time)
	) WITH CLUSTERING ORDER BY (start_time DESC)

Deliverable
---------------

	Week1: Figure out project architecture, data source, determine the requirements and the functionalities to implement
	Week2: Each team member starts implementing their own module
	Week3: Each team member finishes their own module
	Week4: Testing, Report documenting		
	
	Detail Ownerships:
	
		Tongzhou Zhou: 
		Week 1: Set up Kafka Cluster, Cassandra Cluster in AWS
		Week 2: Starts implement data transformation layer, Set up Kafka Connect to load data from Kafka Cluster to Cassandra Cluster 
		Week 3: Finishes implement data transformation layer: 
			(1) Aggregate the data into formats to support the Cassandra data schemas in (2)
			(2) Configure Cassandra data schema to support:
				a: Top 10 highest rating movie by a given month
				b: Top 10 rated movie by a given month
				c: Top rated month by a movie		
		Week 4: Starts and finishes unit testing
		
		Bin Shi: Data ingestion using kafka
		Week 1: Produce data to kafka [80% completed]
				Send movie title data [done]
				Send rating datea simulating the streaming [80%]
		Week 2: Add error/exception handling and more comments in the source code
		Week 3: 
		Week 4: 
		
		Albert:
		Week 1: Build database to store data
		Week 2: design analyst algorithm, optimize database if needed
		Week 3: 
		Week 4: 
		
		Anthony: Data visualization 
		Week 1: Determine the requirements to implement, get ready to fulfill the Nodejs module features; Data cleaning.
		Week 2: Setup backend for data visualization; simple front end to display data
		Week 3: 
		Week 4: 


​		

