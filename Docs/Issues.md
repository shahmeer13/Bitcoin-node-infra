# Issues & Fixes

## Prometheus
- **Problem**: Bitcoin job was DOWN.
- **Fix**: Restarted Bitcoin Exporter with correct RPC credentials.

## Bitcoin Node
- **Problem**: "Cannot obtain a lock on data directory".
- **Fix**: Another `bitcoind` process was running. Stopped it before restarting.

## HAProxy
- **Problem**: HAProxy service failed due to wrong mode.
- **Fix**: Changed `mode http` → `mode tcp`.

- **Problem**: Backends marked as DOWN.
- **Fix**: Corrected backend server ports (8332, 8336).

## Grafana
- **Problem**: Query `up{job="bitcoin"}` returned no data.
- **Fix**: Checked Prometheus targets, fixed job label in query.
