# DevOps Monitoring with Prometheus, Grafana & Node Exporter

This project sets up a **server monitoring stack** using:
- **Prometheus** → Metrics collection
- **Node Exporter** → System metrics exporter
- **Grafana** → Metrics visualization

The setup is designed to run on **AWS EC2** using **Docker Compose** and stores configuration in this GitHub repository for easy redeployment.

---

## 📌 Features
- **System Metrics Monitoring**: CPU, RAM, Disk, Network
- **Prebuilt Grafana Dashboard** (ID 1860 - Node Exporter Full)
- **Docker Compose Deployment**
- **AWS EC2 Ready** Setup
- **GitHub Version Control** for configs

---

## 🖥 Architecture
[Node Exporter] ---> [Prometheus] ---> [Grafana]

yaml
Copy
Edit
- **Node Exporter** runs on the server to collect hardware/system metrics.
- **Prometheus** scrapes metrics from Node Exporter.
- **Grafana** visualizes Prometheus metrics using dashboards.

---

## ⚙ Prerequisites
1. **AWS EC2 Instance** (Ubuntu 22.04 recommended)
2. **Security Group Rules**:
   - TCP 22 → SSH
   - TCP 3000 → Grafana
   - TCP 9090 → Prometheus
   - TCP 9100 → Node Exporter
3. **Docker & Docker Compose Installed**
4. **Git Installed**

---

## 🚀 Deployment Steps

### 1. Clone the Repository
```bash
git clone https://github.com/Sudhansu-12/Devops-monitoring.git
cd Devops-monitoring
2. Start the Monitoring Stack
bash
Copy
Edit
docker-compose up -d
3. Verify Services
bash
Copy
Edit
docker ps
You should see:

prometheus

grafana

node_exporter

🌐 Access the Services
Prometheus → http://<EC2_PUBLIC_IP>:9090

Node Exporter → http://<EC2_PUBLIC_IP>:9100/metrics

Grafana → http://<EC2_PUBLIC_IP>:3000

Default login: admin / admin

📊 Grafana Setup
Login to Grafana at http://<EC2_PUBLIC_IP>:3000

Add Prometheus as a data source:

URL: http://prometheus:9090

Import Dashboard:

Go to + → Import

Enter dashboard ID: 1860

Select the Prometheus data source and click Import

📁 Project Structure
bash
Copy
Edit
.
├── docker-compose.yml        # Docker Compose services
├── prometheus.yml            # Prometheus config file
└── README.md                 # Project documentation
🛠 Stopping the Stack
bash
Copy
Edit
docker-compose down
📌 Future Improvements
Add Alertmanager for alerts (Slack, Email)

Add Loki for log aggregation

Add Persistent Volumes for long-term metrics storage
