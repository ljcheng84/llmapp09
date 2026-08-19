# Use a lightweight, secure base image to pass the Trivy scan
FROM python:3.12-slim-bookworm

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Install system updates
RUN apt-get update && apt-get upgrade -y && \
    rm -rf /var/lib/apt/lists/*

# Copy the requirements file from your folder into the container
COPY requirements.txt .

# Install your Python packages
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# Copy the rest of your app code
COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
