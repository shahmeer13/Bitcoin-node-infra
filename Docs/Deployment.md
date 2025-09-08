# Deployment Guide

This document explains the step-by-step process used to deploy the Bitcoin full node infrastructure with monitoring and load balancing.

---

## 1. Bitcoin Node
- Installed Bitcoin Core v26.1.
- Configured `bitcoin.conf` with RPC enabled and pruning.
- Created a `systemd` service for auto-restart on boot.

📄 Config file: [../configs/bitcoin.conf](../configs/bitcoin.conf)

### Verification
- `systemctl status bitcoind` → service running
- `bitcoin-cli getblockchaininfo` → returns blockchain sync info

---

## 2. Prometheus & Exporters
- Installed Prometheus.
- Added scrape targets:
  - `localhost:9090` (Prometheus itself)
  - `localhost:9100` (Node Exporter for system metrics)
  - `localhost:9332` (Bitcoin Exporter for blockchain metrics)

📄 Config file: [../configs/prometheus.yml](../configs/prometheus.yml)

### Verification
- Visit `http://<SERVER_IP>:9090/targets` → all jobs UP
- Query example: `bitcoin_blocks`

---

## 3. Grafana
- Installed Grafana on Ubuntu.
- Added Prometheus as a data source.
- Imported dashboards:
  - Node Exporter Full (CPU, RAM, Disk, Network)
  - Bitcoin custom panels (block height, peers, mempool size)

### Verification
- Visit `http://<SERVER_IP>:3000` → Grafana login
- Panels display system + Bitcoin metrics

---

## 4. HAProxy
- Configured HAProxy for TCP load balancing of Bitcoin RPC:
  - Frontend: port 8334
  - Backends: 8332, 8336
- Enabled HAProxy stats UI on port 8404.

📄 Config file: [../configs/haproxy.cfg](../configs/haproxy.cfg)

### Verification
- `haproxy -c -f /etc/haproxy/haproxy.cfg` → config valid
- `curl` to `http://127.0.0.1:8334/` → returns Bitcoin RPC response
- Visit `http://<SERVER_IP>:8404/stats` → stats dashboard

---

## 5. Security
- Enabled UFW firewall.
- Allowed only required ports:
  - 8332, 8336 → Bitcoin RPC
  - 8334 → HAProxy frontend
  - 8404 → HAProxy stats
  - 9090 → Prometheus
  - 9100 → Node Exporter
  - 9332 → Bitcoin Exporter
  - 3000 → Grafana

### Verification
- `ufw status` → shows allowed services and ports
