# Use official Python image from the Docker Hub
FROM python:3.10-slim

# Set environment variables to prevent Python from writing .pyc files
# and to ensure output is logged in real time.
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set the working directory in the container to /app
WORKDIR /app

# Install dependencies
# First, copy the requirements.txt file
COPY requirements.txt .

# Install the Python packages listed in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Collect static files (if applicable)
RUN python manage.py collectstatic --noinput

# Copy the entire project folder into the /app folder in the container
COPY . .

# Expose port 8000 (default port for Django)
EXPOSE 8000

# Set the default command to run when starting the container:
# This will run the Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]