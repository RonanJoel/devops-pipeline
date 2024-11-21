# Use a base Python image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the application files into the container
COPY . /app

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port on which the application will listen
EXPOSE 5000

# Command to run the application
CMD ["python", "app.py"]  # Adjust this if your main file is different
