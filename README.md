# Kafka-setup-on-AWS
Apache Kafka Setup on AWS.

Prerequisites
# 1) Create an EC2 Instance
Steps for creating an AWS instance are clearly mentioned in the official AWS documentation; choose must be instance Type: t2.medium not t2:micro bcz very less of memory. but Kafka is using more memory configuration.

# 2) Install Java 8
Since we will be working with the Kafka binary for Scala 2.12, our instance must have Java 8. By default, the EC2 instances have Java 7. You may check and upgrade the Java version to 8 on your instance by following the steps here.

After installing Java 8, follow the steps mentioned below in sequence to start Kafka on your instance.

# Step 1: Downloading and Extracting Kafka
Download kafka_2.12-2.2.2.tgz
 #wget https://downloads.apache.org/kafka/2.2.2/kafka_2.12-2.2.2.tgz

# Step 2: Extract the .tgz file

#tar -xzf kafka_2.12-2.2.2.tgz

# Step 3: Since the zip is of no use now, we remove it:

#rm kafka_2.12-2.2.2.tgz

# Step 4: Got to kafka_2.12-2.2.2 folder

# START ZOOKEEPER
#bin/zookeeper-server-start.sh config/zookeeper.properties

# START KAFKA-SERVER
#bin/kafka-server-start.sh config/server.properties

# CREATE TOPIC ON AWS
#bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test

# List of TOPIC inside ZOOKEEPER
#bin/kafka-topics.sh --zookeeper localhost:2181 --list

# PRODUCER 
#bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test2

# CONSUMER
#bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test2 --from-beginning
