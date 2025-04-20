📊 Prometheus-Based Real-Time System Monitoring Dashboard
This project implements a real-time system monitoring dashboard using Prometheus, an open-source monitoring and alerting toolkit. The dashboard captures live metrics such as CPU usage, memory utilization, and more, providing insights through Prometheus’ native UI.

🔧 Project Overview
Prometheus scrapes metrics from various exporters at regular intervals.

These metrics are queried and visualized using Prometheus’ built-in graphing interface.

The setup runs inside a Docker container, demonstrating how containerization simplifies deployment and isolation of monitoring tools.

🐳 Docker & Containerization
Docker is used to containerize Prometheus, which offers several benefits:

✅ Portability – runs the same across environments

🔒 Isolation – Prometheus runs in its own environment without affecting the host system

⚙️ Ease of deployment – a single command sets up the service

♻️ Reproducibility – consistent behavior across setups

Example Docker Command:

bash
Copy
Edit
docker run -d --name prometheus \
  -p 9090:9090 \
  -v /full/path/to/prometheus.yml:/etc/prometheus/prometheus.yml \
  prom/prometheus
Make sure to replace /full/path/to/prometheus.yml with the actual absolute path to your configuration file.

📁 prometheus.yml Configuration
A basic example:

yaml
Copy
Edit
global:
  scrape_interval: 5s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
This config tells Prometheus to scrape its own metrics and system metrics exposed by node_exporter.

🚀 Getting Started
Install Docker and ensure it is running.

Download or create the prometheus.yml file as shown above.

Run the Prometheus container using the command provided.

Visit http://localhost:9090 to access the Prometheus UI.

🔍 Example Prometheus Queries

Metric	Query Example
CPU Usage	rate(node_cpu_seconds_total{mode="user"}[1m])
Memory Usage	node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes
Disk Usage	node_filesystem_avail_bytes / node_filesystem_size_bytes
Uptime	node_time_seconds - node_boot_time_seconds
📈 Dashboard Output
Using Prometheus' UI, you can:

Run real-time queries on metric data

Plot metrics on graphs over time

Monitor resource consumption and performance trends

✅ Applications
Local development system monitoring

DevOps observability and metric collection

Learning Prometheus and Docker fundamentals


![Screenshot 2025-04-20 150617](https://github.com/user-attachments/assets/3ed92916-7114-4f19-b53b-56198aa57bff)
![Screenshot 2025-04-20 150440](https://github.com/user-attachments/assets/97b7dfff-469c-4189-a64d-11ecd5837c3a)
![Screenshot 2025-04-20 150354](https://github.com/user-attachments/assets/7868c87a-1aae-4563-a530-ad564d889895)
![Screenshot 2025-04-20 150251](https://github.com/user-attachments/assets/d65808e9-1e05-4f7f-ae77-94d729341dd5)
![Screenshot 2025-04-19 182940](https://github.com/user-attachments/assets/77435b99-cd4a-48c9-a77d-90a59dd60a44)



Lightweight alternative to full observability stacks

