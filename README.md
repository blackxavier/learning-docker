# Docker Compose Overview

This Docker Compose configuration sets up a multi-container environment for a Django web application, Nginx as a reverse proxy, PostgreSQL database, pgAdmin for database management, Dozzle for viewing Docker logs, Prometheus for monitoring, Node Exporter for exporting machine metrics, Nginx Exporter for exporting Nginx metrics, and Grafana for visualization of metrics.

## Services:

1. **Web Service (Django):**

   - Builds the Django web application.
   - Uses Gunicorn as the application server.
   - Exposes port 8000.
   - Depends on the PostgreSQL database.

2. **Nginx:**

   - Builds the Nginx service.
   - Acts as a reverse proxy for the Django application.
   - Serves static files.
   - Exposes port 80.
   - Depends on the web service.

3. **PostgreSQL Database:**

   - Uses the official PostgreSQL 12 image.
   - Restarts always.
   - Defines environment variables for PostgreSQL configuration.
   - Exposes port 5432.
   - Has a health check to ensure PostgreSQL is ready.

4. **pgAdmin:**

   - Manages PostgreSQL databases through a web interface.
   - Uses the pgAdmin 4 image.
   - Exposes port 5050.

5. **Dozzle:**

   - Displays Docker container logs in a web interface.
   - Uses the Dozzle image.
   - Exposes port 9999.
   - Mounts the Docker socket for access.

6. **Prometheus:**

   - Monitors the Docker services.
   - Uses the Prometheus image.
   - Exposes port 9090.
   - Mounts a configuration file.

7. **Node Exporter:**

   - Exports machine metrics for Prometheus.
   - Uses the official Node Exporter image.
   - Exposes port 9100.

8. **Nginx Exporter:**

   - Exports Nginx metrics for Prometheus.
   - Uses the official Nginx Prometheus Exporter image.
   - Exposes port 9913.
   - Depends on the Nginx service.

9. **Grafana:**
   - Visualizes metrics collected by Prometheus.
   - Uses the Grafana image.
   - Exposes port 3000.
   - Mounts configuration files.

## Volumes:

- **postgres_data_prod:** Volume for persisting PostgreSQL data.
- **static_volume:** Volume for serving static files.

### Usage:

1. Run the Docker Compose file after cloning the repo using:
   ```bash
   docker-compose - f docker-compose.prod.yml up --build
   ```
2. Access services:
   - Web Application: [http://localhost:8000](http://localhost:8000)
   - Nginx: [http://localhost:80](http://localhost:80)
   - pgAdmin: [http://localhost:5050](http://localhost:5050)
   - Dozzle: [http://localhost:9999](http://localhost:9999)
   - Prometheus: [http://localhost:9090](http://localhost:9090)
   - Grafana: [http://localhost:3000](http://localhost:3000) (Default login: admin/admin)

**Note:** Make sure to customize environment variables and configurations based on your application needs.
