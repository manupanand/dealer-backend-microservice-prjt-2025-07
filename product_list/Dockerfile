# Use a slim base image
FROM python:3.8-slim-buster

# Set the working directory inside the container
WORKDIR /app

# Copy requirements file first to leverage Docker cache for dependencies
COPY requirements.txt .

# Install Python dependencies
RUN pip3 install --no-cache-dir -r requirements.txt

# Copy the remaining application files
COPY . .

# Expose the default Flask port
EXPOSE 5000

# Run the Flask application using Gunicorn for better production performance
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "app:app"]
