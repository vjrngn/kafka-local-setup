#### Working with Kafka CLI
___
###### Topics
<!-- ###### List topics -->
```sh
# List all topics
kafka-topics.sh --bootstrap-server localhost:9092 --list

# Create a topic
kafka-topics.sh --bootstrap-server localhost:9092 --topic user-activity --create --partitions 3 --replication-factor 1

# Describe a topic
kafka-topics.sh --bootstrap-server localhost:9092 --topic user-activity --describe

# Delete a topic
kafka-topics.sh --bootstrap-server localhost:9092 --topic user-activity --delete
```

###### Console Producer
```sh
# Start console producer
kafka-console-producer.sh --broker-list localhost:9092 --topic user-activity

# Start console producer with custom property
kafka-console-producer.sh --broker-list locahost:9092 --topic user-activity --producer-property acks=all
```

###### Console Consumer
```sh
# Start a console consumer (by default listens to latest messages)
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic user-activity

# Start a console consumer to listen from the earliest message
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic user-activity --from-beginning

# Start a console consumer as part of a group
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic user-activity --group email-notification-worker
```

###### Consumer groups
```sh
# List all consumer groups
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list

# Describe consumer group
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group email-notification-worker --describe

# Reset consumer group offset for a specific topic
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group email-notification-worker --reset-offsets --to-earliest --execute --topic user-activity
```