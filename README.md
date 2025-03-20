# 🚀 Docker Observability: Monitor Containers with cAdvisor, Prometheus, and Grafana  

![Docker-Observability drawio](https://github.com/user-attachments/assets/806adab5-7a37-4d8d-b446-1ad96b01becd)

## 📌 Overview  
This project provides a **complete monitoring stack** for Docker containers using:  
✅ **cAdvisor** - Collects real-time container metrics  
✅ **Prometheus** - Stores and queries time-series data  
✅ **Grafana** - Visualizes metrics with interactive dashboards  

With this setup, you can **track CPU, memory, disk, and network usage** for your containers in real time! 🚀  

---

## 📁 File Structure  

```
📂 monitoring/
 ├── 📜 docker-compose.yml    # Defines cAdvisor, Prometheus, and Grafana services
 ├── 📜 prometheus.yml        # Prometheus scrape configuration
 ├── 📜 datasources.yml       # Grafana data source config (auto-connects Prometheus)
 ├── 📜 dashboard.json        # Pre-configured Grafana dashboard
 ├── 📜 default.yaml          # Grafana dashboard provisioning
```

---

## 🛠️ Setup & Installation  

### 1️⃣ Clone the Repository  
```sh
git clone https://github.com/hasnain393/docker-observability.git
cd docker-monitoring-stack
```

### 2️⃣ Start the Monitoring Stack  
```sh
docker compose up -d
```

This will start:  
✅ **cAdvisor** → `http://localhost:8080`  
✅ **Prometheus** → `http://localhost:9090`  
✅ **Grafana** → `http://localhost:3000` (Login: `admin / admin`)  

---

## 📊 Grafana Dashboard Setup  
1️⃣ **Open Grafana** → `http://localhost:3000`  
2️⃣ **Go to Dashboards → Import**  
3️⃣ **Upload `dashboard.json` or `Docker Monitoring Test.json`**  
4️⃣ **Enjoy real-time container metrics! 🚀**  

---

## 📌 Useful PromQL Queries  

🔹 **CPU Usage:**  
```promql
rate(container_cpu_usage_seconds_total{container_label_com_docker_compose_service="your-container-name"}[5m])
```

🔹 **Memory Usage:**  
```promql
container_memory_usage_bytes{container_label_com_docker_compose_service="your-container-name"}
```

🔹 **Network I/O:**  
```promql
rate(container_network_transmit_bytes_total{container_label_com_docker_compose_service="your-container-name"}[5m])
```

---

## 🛠️ Troubleshooting  

### 🔸 No data in Grafana?  
- Check if **cAdvisor is running**:  
  ```sh
  docker ps | grep cadvisor
  ```
- Verify Prometheus is **scraping cAdvisor**:  
  ```sh
  curl http://localhost:8080/metrics | grep container_cpu_usage_seconds_total
  ```
- Restart services:  
  ```sh
  docker-compose restart prometheus cadvisor
  ```

---

## 📜 License  
This project is **open-source** under the **MIT License**. Feel free to contribute!  

---

## 📢 Contribute & Share!  
- Fork the repo & submit PRs 🤝  
- Share with the DevOps community 🚀  
