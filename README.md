# Streaming-bus-data-pipeline
This project implements a real time streaming data pipeline(ETL), using open API of TTC bus called Red bus (http://restbus.info/api/agencies/ttc/routes) to stream bus data for a specific routes. The architecture uses Apache Kafka and Spark Structure Streaming. The data is visualized with Superset which running on docker container.
# Technologies
1. NIFI Version = 1.12.0
2. MySQL-Debezium Version = 1.6
3. Kafka Version = 1.6
4. Spark Version = 3.2.0

