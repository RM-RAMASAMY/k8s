# Use Python as the base image
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy backend requirements and install dependencies
COPY backend/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy backend code
COPY backend/ .

# Install Nginx
RUN apt-get update && apt-get install -y nginx

# Copy frontend files
COPY frontend/index.html /var/www/html/

# Copy Nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Expose ports for both backend and frontend
EXPOSE 5000 80

# Start both services
CMD service nginx start && python app.py