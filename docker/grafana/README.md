# Grafana

Install : https://grafana.com/docs/grafana/latest/setup-grafana/installation/debian/

```bash
sudo systemctl status grafana-server.serice
sudo systemctl enable —now grafana-server.service

sudo lsof -n -P -i | grep grafana
```

Default User & Password : admin / admin

Setting > Add Data Source

Dashboard > import :

https://grafana.com/grafana/dashboards/1860-node-exporter-full/

Dashboard ID : `1860`