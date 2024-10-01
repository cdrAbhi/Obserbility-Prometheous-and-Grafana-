# Stage 1: Build Stage
# Use the official Python image to build dependencies
FROM python:3.9 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy only the requirements file to the container
COPY requirements.txt .

# Install build dependencies (for Alpine compatibility)
RUN apt-get update && apt-get install -y \
    gcc \
    libffi-dev \
    libssl-dev \
    python3-dev \
    && python -m venv /venv \
    && . /venv/bin/activate \
    && pip install --no-cache-dir -r requirements.txt \
    && apt-get remove --purge -y gcc libffi-dev libssl-dev python3-dev \
    && apt-get autoremove -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Stage 2: Final Stage
# Use a minimal Python image for the final container
FROM python:3.9-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy the virtual environment from the build stage
COPY --from=builder /venv /venv

# Copy the application files from the host to the container
COPY . .

# Activate the virtual environment for Python commands
ENV PATH="/venv/bin:$PATH"

# Expose the port the application runs on
EXPOSE 8000

# Command to run the Django application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
