# kafka-first-steps
Kafka First Steps, configuration and most usual commands

The first step to work with the cluster is start zookeeper:

from kafka install directory: ./bin/zookeeper-server-start.sh ./config/zookeeper.properties

Once the zookeper is ready, each of the kafka servers have to be started

from kafka install directory:

./bin/kafka-server-start.sh ./config/server.properties
./bin/kafka-server-start.sh ./config/server-1.properties
./bin/kafka-server-start.sh ./config/server-2.properties

Once the zookeeper and all servers are ready, we can create some topic and send/consume messages from this topic. 

To create a topic:

.bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 3 --partitions 3 --topic test-topic

Connect to a topic to produce messages:

./kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092

Connect to a topic consume messages:

./kafka-console-consumer.sh --topic test-topic --from-beginning --bootstrap-server localhost:9094


As we can see, we have connected to produce messages to localhost:9092 and to consume messages to server localhost:9094, as we have created the topic with 3 partitions and replica-factor 3, each server has a lead partition of the topic and the messages are replicated to all servers.

