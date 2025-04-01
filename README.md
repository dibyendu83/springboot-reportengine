# Spring Boot Report Engine

# Overview

This is a microservice-based application that generates reports asynchronously using Apache Kafka.  
It is designed to scale out dynamically based on CPU load, ensuring efficient and reliable report generation.

## Features

- Asynchronous report generation using Kafka.
- Scales automatically based on CPU load.
- Supports multiple report formats (e.g., PDF, Excel, CSV).
- Spring Boot-based microservice architecture.
- Kafka-based messaging for event-driven processing.

## Tech Stack

- **Backend**: Java 11, Spring Boot 3.x
- **Messaging**: Apache Kafka
- **Database**:  MySQL (configurable)
- **Storage**:  AWS S3 (store the the reports)
- **Containerization**: Docker
- **Monitoring**: Prometheus, Grafana (optional)

## Architecture

1. **Client requests a report** → API accepts the request and pushes it to Kafka.  
2. **Kafka processes the request** → Consumers pick up the task asynchronously.  
3. **Worker nodes generate reports** → Reports are stored in S3 and when completed update the status in DB.  
4. **Client retrieves the report** → Notification sent when ready. 

![Deployment](deployment.png)