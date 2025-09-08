# Bitcoin Node Infrastructure Architecture
This diagram shows the end-to-end Bitcoin node infrastructure. Clients connect via HAProxy for load-balanced RPC access.
Metrics flow from Bitcoin nodes into Prometheus, and the Grafana dashboard visualizes both systems' health and blockchain performance

<img width="969" height="1624" alt="image" src="https://github.com/user-attachments/assets/788e1e56-227c-4961-9ac2-7b7b434fc5f4" />

---

## Notes
- **HAProxy** provides round-robin load balancing, health checks, and stats UI.  
- **Bitcoin Nodes** are pruned full nodes exposing RPC interfaces.  
- **Bitcoin Exporter** converts node metrics into Prometheus-readable format.  
- **Prometheus** scrapes and stores metrics.  
- **Grafana** visualizes performance and blockchain metrics.
