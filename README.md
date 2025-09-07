# Bitcoin Node Infrastructure

🚀 End-to-end Bitcoin full node deployment with monitoring and load balancing.

## Features
- Full Bitcoin Core node with RPC enabled
- Prometheus integration for metrics scraping
- Grafana dashboards for visualization (system metrics + blockchain metrics)
- HAProxy load-balanced RPC frontend (port 8334) with health checks
- Systemd services for automated recovery on reboot
- Firewall (UFW) hardening and access control

## Architecture 

<img width="969" height="1624" alt="image" src="https://github.com/user-attachments/assets/a9d0daa0-ace8-47c4-a848-286113c29f01" />
