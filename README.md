# APACHE_KAFKA-

# Kafka and Zookeeper Docker Configuration

This repository contains a Docker Compose configuration to set up Apache Kafka and Zookeeper using Confluent's Docker images. This setup allows you to run Kafka in a local development environment easily.

## Prerequisites

- Docker: Make sure you have Docker installed on your machine. You can download it from [Docker's official website](https://www.docker.com/get-started).
- Docker Compose: Docker Compose is included with Docker Desktop installations. If you're using Linux, you may need to install it separately. Refer to the [Docker Compose installation guide](https://docs.docker.com/compose/install/) for instructions.

## Getting Started

To get started with Kafka and Zookeeper, follow these steps:

1. **Clone the Repository**

   Clone this repository to your local machine:

   ```bash code:
   git clone https://github.com/yourusername/kafka-docker-setup.git
   cd kafka-docker-setup

2. **Start the Services**

Use Docker Compose to start the Zookeeper and Kafka services:

   bash code:
   docker-compose up -d

This command will start both Zookeeper and Kafka in detached mode.

3. **Accessing Kafka**

Zookeeper will be accessible on port 2181.
Kafka will be accessible on:
Internal Docker network: 9092
Host access from Windows: 29092

**Configuration Details**
The docker-compose.yml file includes the following configurations:

Zookeeper Service:

Image: confluentinc/cp-zookeeper:7.5.0
Container Name: zookeeper
Client Port: 2181

Kafka Service:
Image: confluentinc/cp-kafka:7.5.0
Container Name: kafka
Depends on: Zookeeper
Ports:
*9092 for internal Docker access
*29092 for host access from Windows

Environment Variables:
KAFKA_BROKER_ID: Unique ID for the broker
KAFKA_ZOOKEEPER_CONNECT: Connection string for Zookeeper
KAFKA_LISTENERS: Configures the listeners for Kafka
KAFKA_ADVERTISED_LISTENERS: Advertised listeners for clients
KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: Security protocol mapping
KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: Replication factor for offsets topic
KAFKA_AUTO_CREATE_TOPICS_ENABLE: Enable auto-creation of topics

Stopping the Services:
To stop the services, run:
   docker-compose down
