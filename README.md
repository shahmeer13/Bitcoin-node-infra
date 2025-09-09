# Bitcoin Node Infrastructure 🚀

This project demonstrates the deployment of a Bitcoin full node with production-style infrastructure.
It includes monitoring, load balancing, and security hardening — simulating real-world Web3 / DevOps engineering tasks.



🔑 Features

    • Bitcoin Core v26.1 full node (pruned) with RPC enabled
    •	Prometheus monitoring stack with:
    •	Node Exporter (system metrics)
    •	Bitcoin Exporter (blockchain metrics)
    •	Grafana dashboards for system health + blockchain activity
    •	HAProxy load balancing for Bitcoin RPC with failover and health checks
    •	Firewall (UFW) configured with minimal open ports



📂 Repository Structure

Configs

    • Config files (bitcoin.conf, haproxy.cfg, prometheus.yml)

Docs: 

    • Documentation (Architecture, Deployment, Issues, TOC)
Screenshots:

    •Proof screenshots (node, Prometheus, Grafana, HAProxy, UFW)
README.md 

    • Project overview (this file)

🖼️ Screenshots

	•	Bitcoin Node Running
	•	Prometheus Targets
	•	Grafana System Metrics
	•	Grafana Bitcoin Metrics
	•	HAProxy Stats
	•	Firewall Status
Full details: Screenshots.md



📖 Documentation

	•	Architecture
	•	Deployment Guide
	•	Issues & Fixes
	•	Docs TOC



⚙️ Tech Stack

	•	Ubuntu 22.04 LTS (OVH Bare Metal)
	•	Bitcoin Core v26.1
	•	Prometheus v2.x
	•	Grafana v12.x
	•	HAProxy v2.x
	•	UFW Firewall



📝 Notes

⚠️ The live Bitcoin node was decommissioned after testing.
This repository documents the full deployment process, including configs, screenshots, and verification steps.


👤 About Me

This project was developed as part of my journey into Web3 Infrastructure Engineering & DevOps.
It serves as a portfolio case study demonstrating hands-on infrastructure deployment and operations.

🔧 Key Skills Demonstrated

	•	Blockchain node deployment (Bitcoin Core v26.1)
	•	Configuration management and systemd services
	•	Prometheus + Grafana monitoring stack setup
	•	HAProxy load balancing with health checks
	•	Security hardening (UFW firewall, port restrictions)
	•	Troubleshooting and issue resolution in production-like environments
