# Use Python base image
FROM python:3.9-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /app

# Copy dependencies file first (improves cache layer)
COPY requirements.txt /app/

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the app code
COPY . /app

EXPOSE 5000

# Healthcheck to monitor the app
HEALTHCHECK CMD curl --fail http://localhost:5000/ || exit 1

CMD ["python", "app.py"]
