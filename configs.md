📂 configs/

1. haproxy.cfg (for Bitcoin RPC load balancing)
# HAProxy configuration for Bitcoin RPC Load Balancing

global
    log /dev/log local0
    log /dev/log local1 notice
    daemon

defaults
    log     global
    mode    tcp
    option  tcplog
    timeout connect 5000
    timeout client  50000
    timeout server  50000

frontend btc_rpc_fe
    bind *:8334
    default_backend btc_nodes

backend btc_nodes
    balance roundrobin
    option tcp-check
    server node1 127.0.0.1:8332 check
    server node2 127.0.0.1:8336 check

listen stats
    bind *:8404
    mode http
    stats enable
    stats uri /stats
    stats refresh 10s

2. prometheus.yml (scraping Bitcoin + Node Exporter + Prometheus itself)
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]

  - job_name: "node"
    static_configs:
      - targets: ["localhost:9100"]

  - job_name: "bitcoin"
    static_configs:
      - targets: ["localhost:9332"]


3. Bitcoin.conf (example — sanitized)
# Bitcoin Core configuration
server=1
daemon=1
txindex=0
prune=550

# RPC settings
rpcuser=bitcoinrpc
rpcpassword=YOUR_SECURE_PASSWORD
rpcallowip=127.0.0.1
rpcbind=127.0.0.1
rpcport=8332

    
