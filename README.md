# Docker Compose Project for Django Application

This project uses Docker Compose to manage multiple services for a Django application. It includes the following services:

## Services Overview

### Web Service (Django and Nginx)
- **Service Name:** `web`
- **Description:** Django web service with Gunicorn as the WSGI server.
- **Usage:** Exposes Django application on port 8000.

### PostgreSQL Database
- **Service Name:** `db`
- **Description:** PostgreSQL database service.
- **Usage:** Exposes PostgreSQL on port 5432.

### pgAdmin (PostgreSQL Management Tool)
- **Service Name:** `pgadmin`
- **Description:** pgAdmin service for managing PostgreSQL databases.
- **Usage:** Exposes pgAdmin on port 5050.

### Dozzle (Docker Container Logs Viewer)
- **Service Name:** `dozzle`
- **Description:** Container logs viewer for monitoring Docker containers.
- **Usage:** Exposes Dozzle on port 9999.

### Vector (Logs Shipper)
- **Service Name:** `vector`
- **Description:** Vector service for shipping logs to BetterStack platform.
- **Usage:** Configured to ship logs from Docker containers and Docker daemon.

### Prometheus (Monitoring and Alerting Toolkit)
- **Service Name:** `prometheus`
- **Description:** Prometheus service for monitoring.
- **Usage:** Exposes Prometheus on port 9090.

### Node Exporter (Prometheus Exporter)
- **Service Name:** `node-exporter`
- **Description:** Prometheus exporter for collecting hardware and OS metrics.
- **Usage:** Exposes Node Exporter on port 9100.

### Nginx Exporter (Prometheus Exporter for Nginx)
- **Service Name:** `nginx-exporter`
- **Description:** Prometheus exporter for Nginx metrics.
- **Usage:** Exposes Nginx Exporter on port 9913.

### Grafana (Open-source Platform for Monitoring and Observability)
- **Service Name:** `grafana`
- **Description:** Grafana service for visualization and monitoring.
- **Usage:** Exposes Grafana on port 3000.

## Usage

GitHub Copilot
Sure, here is the modified content in proper Markdown format:

Copy .env.example to .env and adjust the configurations.

Run the services using Docker Compose.

Access the services using the following URLs:

Django Application: http://localhost:8000
pgAdmin: http://localhost:5050
Dozzle: http://localhost:9999
Prometheus: http://localhost:9090
Grafana: http://localhost:3000
Current Issues
Postgres DB Logging Issue
The PostgreSQL database logs an error: "role 'root' does not exist". The database works regardless, but this issue needs to be resolved.

Vector Log Shipping
Shipping logs using Vector still needs a bit of work to ensure all logs are correctly shipped to BetterStack.

Postgres Startup Packet Error
PostgreSQL logs an error: "invalid length of startup packet". This is related to connections to the database, but only the Django service is currently connected.

MongoDB Express Connection Issue
MongoDB Express tries to connect to MongoDB before MongoDB is fully operational, even with the depends_on attribute.

Grafana Configuration
Grafana setup and configuration need further attention to ensure it works correctly with the provided datasources.

Additional Notes
Ensure that Docker and Docker Compose are installed on your system.
Adjust the environment variables in the .env file to match your setup.
The docker-compose.prod.yml file is configured for production use. For development, use the docker-compose.yml file.
Feel free to explore each service in detail. Happy coding! ```