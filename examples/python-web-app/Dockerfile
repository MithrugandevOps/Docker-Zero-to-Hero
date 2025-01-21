FROM ubuntu:22.04

# Set non-interactive mode for apt-get
ENV DEBIAN_FRONTEND=noninteractive

WORKDIR /app

# Copy required files
COPY requirements.txt /app/
COPY devops /app/

# Update and install Python dependencies
RUN apt-get clean && rm -rf /var/lib/apt/lists/* && \
    apt-get update && apt-get install -y python3 python3-pip python3-venv && \
    apt-get clean

SHELL ["/bin/bash", "-c"]

# Create virtual environment and install Python dependencies
RUN python3 -m venv venv1 && \
    source venv1/bin/activate && \
    pip install --no-cache-dir -r requirements.txt

EXPOSE 8000

# Run the application
CMD source venv1/bin/activate && python3 manage.py runserver 0.0.0.0:8000
