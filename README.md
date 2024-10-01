# **Observability Stack for Dockerized Applications**

This project sets up a comprehensive observability stack using Dockerized tools to monitor and visualize system and container metrics, as well as application logs. The stack includes Prometheus for metrics collection, Grafana for visualization, Loki for log aggregation, and other key tools like cAdvisor and Node Exporter.

## **Table of Contents**
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Services](#services)
- [Volumes](#volumes)
- [Network](#network)
- [Monitoring Setup](#monitoring-setup)
- [Contributing](#contributing)
- [License](#license)

---

## **Overview**

In modern DevOps environments, observability is critical for ensuring the health, performance, and resilience of applications and infrastructure. This repository provides a complete observability solution by integrating monitoring, container resource usage tracking, and log aggregation.

The stack includes:
- **Prometheus** for collecting time-series metrics.
- **Grafana** for visualizing metrics and logs.
- **Loki** for centralized log management.
- **cAdvisor** for monitoring container performance.
- **Node Exporter** for exporting system-level metrics.

Additionally, a custom **Notes App** is included to demonstrate how the stack monitors a running application.

---

## **Tech Stack**

- **Docker** & **Docker Compose**: Containerization and orchestration.
- **Prometheus**: Metrics collection and monitoring.
- **Grafana**: Data visualization and dashboard creation.
- **Loki**: Log aggregation and management.
- **Promtail**: Log shipping to Loki.
- **cAdvisor**: Container resource monitoring.
- **Node Exporter**: Hardware and OS metrics exporter.
- **Notes App**: A demo application to showcase observability.

---

## **Features**

- Real-time monitoring of container and system metrics.
- Logs aggregation and searching using Loki.
- Visualize metrics and logs with Grafana dashboards.
- Monitor both infrastructure and application performance.
- Persistent data storage for Prometheus and Grafana.
- Easily extendable to add more services and dashboards.

---

## **Prerequisites**

Before starting, ensure you have the following installed:
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## **Installation**

### Step 1: Clone the repository
```bash
git clone https://github.com/cdrAbhi/Obserbility-Prometheous-and-Grafana-
cd Observability-For-DevOps
```

### Step 2: Install Docker and Docker Compose

```bash
sudo apt-get update
sudo apt-get install docker.io
sudo usermod -aG docker $USER && newgrp docker
sudo apt-get install docker-compose
```

### Step 3: Download Prometheus configuration
```bash
wget https://raw.githubusercontent.com/prometheus/prometheus/main/documentation/examples/prometheus.yml
```

### Step 4: Build and Run the Observability Stack

Run the stack using Docker Compose:
```bash
docker-compose up -d
```

---

## **Usage**

Once the stack is running, you can access the following services:

- **Grafana**: http://localhost:3000 (Default login: `admin` / `admin`)
- **Prometheus**: http://localhost:9090
- **cAdvisor**: http://localhost:8080
- **Node Exporter**: http://localhost:9100/metrics
- **Notes App**: http://localhost:8000

---

## **Services**

- **Grafana**: Visualizes the data from Prometheus and Loki.
- **Prometheus**: Collects time-series metrics from Node Exporter, cAdvisor, and the Notes App.
- **Node Exporter**: Exports hardware and OS-level metrics.
- **cAdvisor**: Monitors container resource usage.
- **Loki**: Aggregates logs.
- **Promtail**: Ships logs to Loki from the container.

---

## **Volumes**

The following volumes ensure persistent storage across container restarts:

- `prometheus_data`: Stores Prometheus data persistently.
- `grafana_data`: Stores Grafana dashboards and data persistently.

---

## **Network**

- `web-network`: A custom bridge network is used for isolation and communication between the containers.

---

## **Monitoring Setup**

### Grafana Dashboards

Grafana can be set up with pre-configured dashboards or manually created dashboards:

1. **Add Data Sources**: 
    - Prometheus and Loki are added as data sources in Grafana.
    - Navigate to **Configuration > Data Sources** and search for **Prometheus** and **Loki**.

2. **Dashboards**:
    - **Manual Creation**: Go to **Dashboard > Create New Dashboard** and build your custom visualizations.
    - **Pre-configured**: Use pre-built templates for common use cases. Import them from the Grafana Labs dashboard library.

---

## **Contributing**

Contributions are welcome! Please submit a pull request or open an issue for any changes or improvements.

---

## **License**

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

This `README.md` provides all the necessary information for setting up and using the observability stack, making it easy for developers and DevOps engineers to follow. You can modify the URLs, project name, and other sections as per your specific requirements.
