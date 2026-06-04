# 🚀 Observability & Monitoring DevOps Stack

![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)

## 📌 Project Overview
This project implements a robust, containerized observability and monitoring infrastructure deployed on an **AWS EC2 instance**. It is designed to track real-time metrics, system health, and container performance across multiple web environments. It also features an automated alerting system that triggers email notifications based on specific thresholds (e.g., High CPU/Memory usage, service downtime).

## 🏗️ Architecture & Tech Stack
* **Infrastructure:** AWS (EC2), Docker & Docker Compose
* **Monitoring & Time-Series DB:** Prometheus
* **Data Visualization:** Grafana
* **Alerting System:** Alertmanager (SMTP configured)
* **Metrics Collectors (Exporters):** Node Exporter, cAdvisor, Blackbox Exporter, JMX Exporter

## 🎯 Monitored Services
The stack actively monitors three distinct application environments to demonstrate versatile observability capabilities:
1. **WordPress (PHP/MariaDB):** Web availability and database metrics.
2. **Django (Python):** Application-level metrics exposed via `/metrics`.
3. **Apache Tomcat (Java):** JVM performance and memory management via JMX.

## ⚙️ How to Run Locally / Deploy
This project uses `.env` files to securely manage database credentials and SMTP configurations. 

1. **Clone the repository:**

    git clone https://github.com/Omarusann/Observability-and-Monitoring.git
    cd Observability-and-Monitoring

2. **Configure Environment Variables:**
    Copy the example environment file and fill in your secure credentials.

    cp .env.example .env

    *Edit the `.env` and `alertmanager/alertmanager.yml` files to include your real passwords and emails.*

3. **Deploy the stack:**

    docker compose up -d

## 🌐 Exposed Ports & Access
Once deployed, the services will be available at `http://<YOUR_SERVER_IP>:<PORT>`:

| Service | Port | Description |
| :--- | :--- | :--- |
| **WordPress** | `80` | Main PHP CMS Site |
| **Django** | `8000` | Python Web Framework |
| **Tomcat** | `8085` | Java Web Server |
| **Grafana** | `3000` | Dashboards & Data Visualization |
| **Prometheus** | `9090` | Time-Series Database & Targets |
| **Alertmanager** | `9093` | Alert Management UI |

## 🛡️ Security Note
All sensitive data (database passwords, API keys, SMTP credentials) has been excluded from this repository using `.gitignore`. Please refer to the `.env.example` file to set up your own environment variables.
