Django, Nginx, PostgreSQL, pgAdmin, Dozzle, and Vector Docker Compose Setup
This Docker Compose configuration sets up a multi-container environment for deploying a Django web application along with Nginx as a reverse proxy, PostgreSQL as the database, pgAdmin for database management, Dozzle for Docker logs visualization, and Vector for log shipping.

Services:

1. web (Django Application)
   Build: Uses a Dockerfile (Dockerfile.prod) to build the Django application.
   Command: Starts the Gunicorn server to run the Django application.
   Volumes: Mounts a volume for static files.
   Expose: Exposes port 8000.
   Environment: Reads environment variables from .env.prod.
   Dependencies: Depends on the db service.
2. nginx (Nginx Reverse Proxy)
   Build: Uses the Nginx configuration from the ./nginx directory.
   Volumes: Mounts a volume for static files.
   Ports: Maps port 80 on the host to port 80 on the container.
   Dependencies: Depends on the web service.
3. db (PostgreSQL Database)
   Image: Uses the PostgreSQL 12 image.
   Restart: Always restarts the container.
   Volumes: Mounts a volume for persisting PostgreSQL data.
   Environment: Sets PostgreSQL user, password, and database.
   Expose: Exposes port 5432.
   Healthcheck: Checks if PostgreSQL is ready.
4. pgadmin (pgAdmin for PostgreSQL)
   Image: Uses the latest pgAdmin image.
   Container Name: Sets the container name to pgadmin.
   Environment: Reads environment variables from .env.prod.pg-admin.
   Ports: Maps port 5050 on the host to port 80 on the container.
   Restart: Always restarts the container.
5. dozzle (Docker Logs Visualization)
   Container Name: Sets the container name to dozzle.
   Image: Uses the latest Dozzle image.
   Volumes: Mounts the Docker socket for log access.
   Ports: Maps port 9999 on the host to port 8080 on the container.
6. vector (Log Shipping with Vector)
   Image: Uses the Timber Vector image (timberio/vector:0.32.1-alpine).
   Container Name: Sets the container name to vector.
   Volumes: Mounts the Vector configuration file (vector.toml) and the Docker socket.
   Dependencies: Depends on the nginx service.
   Volumes:
   postgres_data_prod: Volume for persisting PostgreSQL data.
   static_volume: Volume for storing static files.
