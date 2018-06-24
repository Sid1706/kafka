# kafka

How to setup this code -

1) Make sure Docker is up and running.
2) Run the below command to run the kafka on local docker 
           docker run --rm -it \
           -p 2181:2181 -p 3030:3030 -p 8081:8081 \
           -p 8082:8082 -p 8083:8083 -p 9092:9092 \
           -e ADV_HOST=127.0.0.1 \
           landoop/fast-data-dev
 
 After this step - run the below command 
  docker ps 
  take the container Id and run the below commmand - 
  docker exec -it <container_id> bash
  
  
3) Browse the 127.0.0.1:3030 . this will open a UI for the kafka 
4) With the above mentioned commands you will have a local docker running on your machine.   

5) Create a topic (first_topic)  with the below command - 

kafka-topics --zookeeper 127.0.0.1:2181 --create --topic first_topic --partitions 3 --replication-factor 1
kafka-topics --zookeeper 127.0.0.1:2181  --list

kafka-topics --zookeeper 127.0.0.1:2181  --topic first_topic --describe

kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic
kafka-console-consumer --broker-list 127.0.0.1:9092 --topic first_topic

  
