>cd to kafka home directory

to start zookeeper:
>bin/zookeeper-server-start.sh config/zookeeper.properties

to start the broker:
>bin/kafka-server-start.sh config/server.properties

to create multiple brokers, create server-1.properties and so on
set different broker id, port, log.dirs for each broker
start them using above command as: bin/kafka-server-start.sh config/server-1.properties

to create topics:
>bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic user-clicks
>bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic user-location
>bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic outputTopic1
>bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic outputTopic2
can set the partitions and replication-factor if you have multiple brokers

To run the application:
After extracting
>cd to kafka-streaming
>gradle wrapper
>./gradlew build
>cd kafka-streaming/build/scripts


To run the producer:
> ./kafka-streaming producer

To create streams and join:
For KStream-KTable join:
> ./kafka-streaming join

For KStream-KStream join:
>./kafka-streaming windowedjoin

To run the consumer:
> ./kafka-streaming consumer [outputTopic] [groupid]
(outputTopic1 for KStream-KTable join: Join.java, outputTopic2 for KStream-KTable windowedjoin: WindowedJoin.java)

