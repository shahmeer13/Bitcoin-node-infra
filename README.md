# Bitcoin Node Infrastructure

🚀 End-to-end Bitcoin full node deployment with monitoring and load balancing.

## Features
- Full Bitcoin Core node with RPC enabled
- Prometheus integration for metrics scraping
- Grafana dashboards for visualization (system metrics + blockchain metrics)
- HAProxy load-balanced RPC frontend (port 8334) with health checks
- Systemd services for automated recovery on reboot
- Firewall (UFW) hardening and access control

## 📂 Repository Structure

This repository is organized for clarity and reproducibility.  
Each folder contains the necessary configurations, documentation, and evidence (screenshots) required to demonstrate the complete Bitcoin node infrastructure setup.

├── README.md                     # High-level project overview, features, usage
│
├── architecture/                 # System design & topology diagrams
│   ├── diagram.png                # Visual architecture diagram (HAProxy, Nodes, Prometheus, Grafana)
│   └── ascii-architecture.md      # ASCII diagram with description for quick reference
│
├── configs/                      # Service configuration files
│   ├── haproxy.cfg                # HAProxy load balancer config (round-robin RPC + health checks)
│   ├── prometheus.yml             # Prometheus scrape config for Node & Bitcoin metrics
│   └── bitcoin.conf               # Example Bitcoin Core RPC config (sanitized)
│
├── screenshots/                  # Monitoring and verification evidence
│   ├── prometheus-targets.png     # Prometheus targets page (all jobs UP)
│   ├── grafana-node-dashboard.png # Grafana Node Exporter dashboard (system metrics)
│   ├── grafana-bitcoin-dashboard.png # Grafana Bitcoin exporter metrics (block height, peers, mempool)
│   └── haproxy-stats.png          # HAProxy stats UI (backend health + failover proof)
│
└── docs/                         # Deployment documentation and logs
└── deployment-steps.md        # Step-by-step deployment notes with commands & troubleshooting
