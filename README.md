# Tikal Microservices Workshop Parent Page

This is a "Parent" repository page link, that will help you to navigate the various micro services we use in “Tikal micorservices workshop”.

How to run it :

1. Run the EC2 instance (from the AWS console)
2. ssh to the instance.
3. As MongoDB is not running as a service run it as follow : mongod --dbpath /data/db --smallfiles &
4. Run Kafka
  * cd /home/ec2-user/kafka_2.11-0.8.2.2/
  * ./bin/zookeeper-server-start.sh config/zookeeper.properties &
  * ./bin/kafka-server-start.sh config/server.properties &
  * Make sure you have the three needed topics, by running:  `./bin/kafka-topics.sh --list --zookeeper localhost:2181`
  * If they are one of them is missing you can add them as follow
  ```
  bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic ft-gps
  bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic ft-raw-gps
  bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic ft-segments
 ```
5. Run the UI node:
  * cd /home/ec2-user/fleettracker/ft-gps-tracker-ui
  * nohup node server.js &
6. Run all services
  * cd /home/ec2-user/fleettracker
  * ./run_all.sh 
7. Run firehose
  * cd /home/ec2-user/fleettracker/ft-gps-firehose
  * ./run-bin/gps-firehose.sh
Here are the links:

* https://github.com/tikalk/ft-gps-firehose
* https://github.com/tikalk/ft-gps-service
* https://github.com/tikalk/ft-management
* https://github.com/tikalk/ft-analytics
* https://github.com/tikalk/ft-segments-service
* https://github.com/tikalk/ft-gps-tracker-ui
* https://github.com/tikalk/ft-device-manager
* https://github.com/tikalk/ft-geocoder-facade
* https://github.com/tikalk/ft-notifications

