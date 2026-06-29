# Prometheus + Grafana + Loki Observability Stack
### Containerized Monitoring & Log Aggregation for NVIDIA Jetson Edge Devices — Indian Railways

---

## Overview

This repository contains the complete observability stack deployed for monitoring
75–85 NVIDIA Jetson Orin NX edge devices across PVIS-1 and PVIS-2 Indian Railways
monitoring sites.

All metrics and logs are routed securely over OpenVPN tunnels to AWS EC2 —
with zero public internet exposure.

---

## Architecture
---

## Stack Components

| Component | Purpose |
|---|---|
| Prometheus | Metrics collection & storage |
| Grafana | Dashboards & threshold alerting |
| Loki | Log aggregation |
| Promtail | Log shipping agent on Jetson devices |
| Node Exporter | System metrics (CPU, RAM, disk, network) |

---

## Metrics Monitored

- CPU utilization per Jetson device
- Memory pressure & usage
- Disk usage & I/O
- Network I/O (OpenVPN tunnel traffic)
- Device uptime & availability
- OpenVPN tunnel connectivity status

## Logs Collected

- System logs (syslog)
- Application logs
- OpenVPN connection logs

---

## Grafana Alerting Rules

| Alert | Threshold | Action |
|---|---|---|
| High CPU | > 85% for 5 mins | Notify on-call engineer |
| Low Disk | < 10% free | Notify on-call engineer |
| Device Offline | No metrics for 2 mins | Immediate alert |

---

## Deployment

### Prerequisites
- Docker & Docker Compose installed on AWS EC2
- OpenVPN server running with Jetson devices connected
- Node Exporter installed on each Jetson device

### Run the stack

```bash
# Clone the repository
git clone https://github.com/VeLu-AWS/prometheus-grafana-loki-stack.git
cd prometheus-grafana-loki-stack

# Start all services
docker-compose up -d

# Check running containers
docker-compose ps

# View logs
docker-compose logs -f
```

### Access

| Service | URL |
|---|---|
| Grafana | http://your-ec2-ip:3000 |
| Prometheus | http://your-ec2-ip:9090 |
| Loki | http://your-ec2-ip:3100 |

---

## Project Context

| Detail | Info |
|---|---|
| **Deployed at** | Patil Rail Infrastructure Pvt Ltd |
| **Use case** | Indian Railways PVIS-1 & PVIS-2 monitoring |
| **Edge devices** | 75–85 NVIDIA Jetson Orin NX |
| **Cloud** | AWS EC2 — Mumbai (ap-south-1) |
| **VPN** | OpenVPN TAP/TUN with CCD static IPs |
| **Migration** | On-premises → AWS EC2 with EBS storage |

---

## Author

**C Sengottuvelu**
AWS Cloud & DevOps Engineer | SAA-C03 Certified
Bengaluru, India
