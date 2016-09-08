# Docker for MongoDB, Apache Spark and Apache Zeppelin.

## For demo purposes only..

An example of using docker-compose to set up a single [Apache Spark](http://spark.apache.org/) node via [Apache Zeppelin](http://zeppelin.apache.org/) connecting to [MongoDB](https://www.mongodb.com/) via the [MongoDB Spark Connector](https://github.com/mongodb/mongo-spark).

### Starting up 

To get running :

 1. `docker-compose up -d`
    In the background the MongoDB instance will be running in one container and Apache Zeppelin and Spark on another.
 2. Goto: [localhost:8080](http://localhost:8080) to load the Zeppelin
 3. Add the MongoDB Spark Connector to the Spark interpreter: `org.mongodb.spark:mongo-spark-connector_2.11:2.0.0-rc0`
 4. Look at an existing notebook or create your own.


### Todos

  - [ ] Add a Standalone spark instance
  - [ ] Set the environment variable for `SPARK_HOME`
  - [ ] Add the MongoDB Spark Connector package to `SPARK_SUBMIT_OPTION`
