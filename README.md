# Docker Compose Project

This project uses Docker Compose to manage multiple services. It includes the following services:

## Web Service (Django and Nginx)

- **Service Name:** `web`
- **Description:** Django web service with Nginx as a reverse proxy and static files server.
- **Usage:** Exposes Django application on port 8000.

## PostgreSQL Database

- **Service Name:** `db`
- **Description:** PostgreSQL database service.
- **Usage:** Exposes PostgreSQL on port 5432.

## pgAdmin (PostgreSQL Management Tool)

- **Service Name:** `pgadmin`
- **Description:** pgAdmin service for managing PostgreSQL databases.
- **Usage:** Exposes pgAdmin on port 5050.

## Dozzle (Docker Container Logs Viewer)

- **Service Name:** `dozzle`
- **Description:** Container logs viewer for monitoring Docker containers.
- **Usage:** Exposes Dozzle on port 9999.

## Vector (Logs Shipper)

- **Service Name:** `vector`
- **Description:** Vector service for shipping logs to BetterStack platform.
- **Usage:** Exposes Vector for log shipping.

## MongoDB Database

- **Service Name:** `mongodb`
- **Description:** MongoDB database service.
- **Usage:** Exposes MongoDB on port 27017.

## MongoDB Express (MongoDB Web-based UI)

- **Service Name:** `mongodb-express`
- **Description:** Web-based UI for MongoDB management.
- **Usage:** Exposes MongoDB Express on port 8081.

## Node App

- **Service Name:** `node-app`
- **Description:** Node.js application with MongoDB connection.
- **Usage:** Exposes Node.js application on port 3000.

## Prometheus (Monitoring and Alerting Toolkit)

- **Service Name:** `prometheus`
- **Description:** Prometheus service for monitoring.
- **Usage:** Exposes Prometheus on port 9090.

## Node Exporter (Prometheus Exporter)

- **Service Name:** `node-exporter`
- **Description:** Prometheus exporter for collecting hardware and OS metrics.
- **Usage:** Exposes Node Exporter on port 9100.

## Nginx Exporter (Prometheus Exporter for Nginx)

- **Service Name:** `nginx-exporter`
- **Description:** Prometheus exporter for Nginx metrics.
- **Usage:** Exposes Nginx Exporter on port 9913.

## Grafana (Open-source Platform for Monitoring and Observability)

- **Service Name:** `grafana`
- **Description:** Grafana service for visualization and monitoring.
- **Usage:** Exposes Grafana on port 3000.

## Additional Services

### MongoDB Services

- **Services:** `mongodb`, `mongodb-express`, `node-app`
- **Description:** MongoDB services for a Node.js application.

### Prometheus Services

- **Services:** `prometheus`, `node-exporter`, `nginx-exporter`
- **Description:** Prometheus and related exporters for monitoring.

## Usage

1. Clone the repository.
2. Copy `.env.example` to `.env` and adjust the configurations.
3. Run `docker-compose -f docker-compose.prod.yml up -d` to start the services.

Feel free to explore each service in detail. Happy coding!

## Current Issues

1. Postgres DB keeps logging - role 'root' does not exist. Still figuring out how to take care of this. The db works regardless though.
2. Shipping logs using vector still needs a bit of work.
3. Postgres has a new error. Though at the `LOG` severity - invalid length of statup packet. The internet says it has to do with connections to the DB but only the django service id currently connected.
4. Mongodb express keeps trying to connect to mongo before mongo is fully operational even with the `depends_on` attribute
5. Graphana is a pain.
