
# Use an official Python runtime as a parent image
FROM python:3.11.4-slim-buster

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set work directory
WORKDIR /app

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends netcat

# Copy requirements file and install dependencies
COPY requirements.txt /app/requirements.txt
RUN pip install --upgrade pip && pip install -r requirements.txt
# install dependencies, etc.
RUN apt-get update && apt-get install -y tree && tree .

# Copy project files
COPY . /app/
# Debug: print files and working dir
RUN find . -type f && pwd && ls -ltr
# Fix Windows line endings and set executable permission on the entrypoint script
RUN sed -i 's/\r//g' backend/entrypoint/entrypoint.sh && \
    chmod +x backend/entrypoint/entrypoint.sh

# Set the entrypoint
ENTRYPOINT ["/app/backend/entrypoint/entrypoint.sh"]