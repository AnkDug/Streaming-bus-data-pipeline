# Streaming-bus-data-pipeline
This project implements a real time streaming data pipeline(ETL), using open API of TTC bus called Red bus (http://restbus.info/api/agencies/ttc/routes) to stream bus data for a specific routes. The architecture uses Apache Kafka and Spark Structure Streaming. The data is visualized with Superset which running on docker container.

## Technologies
1. NIFI Version = 1.12.0
2. MySQL-Debezium Version = 1.6
3. Kafka Version = 1.6
4. Spark Version = 3.2.0

## Workflow
1. Nifi extract the data from TTC Rest API and files to the MySQL database in the form of table. It makes automation for the conversion and movement of data between systems tby connecting multiple processors.
2. Further, Debezium as distributed platform turns existing databases in MySQL into event streams. Applications quickly react to each row-level change (CDC) in the databases and load them into Kafka topics.
3. Spark will consume the data from kafka and transform it with the help of given schema.
4. Data will start processing with Hudi by spark-master and convert it to parquet files. Existing records are stored in metadat(commit file) and after for every new records there will be new parquet files.
5. Those parquet file will be stored in S3 bucket.
6. Athena will create the table format of the parquet files and can query it.
7. Superset running on docker container will read the data from athena and visualize it.

## Files included in repository
  . Nifi Flow
  . bash scripts for creating necessary resources on EC2 like docker containers and AWS
  . pyspark script
  . Superset dashboard

## Additinal notes
  To visualize map on the dashboard, need to configure the mapbox API in superset. Please refer sources for the same.

## Sources
  This project is inspired by Edwin Guo's lecture and Spark Streaming with Kafka-Connect Debezium Connector by @Suchit Gupta.
  Configuring Mapbox API in super set by techsapphire on Youtube.

