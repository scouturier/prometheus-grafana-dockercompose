# Deploy Prometheus, Node-exporter, Alert Manger & Grafana

This will show you how to easily deploy Prometheus along with Node-exporter, Alertmanager & Grafana using docker-compose. I usually recommend deploying theses within a Kubernetes/OpenShift cluster but there is a few occasions where this would need to be deployed outside, especially if it was going to be a monitoring solution for such clusters.

### Images
We will be using the following products images from hub.docker.com:
- prom/prometheus
- prom/node-exporter
- prom/alertmanager
- grafana/grafana

### Configuration
The configuration files should work out of the box, but you can modify the following to suit your needs:

| Container | Config |
| ------------- |:-------------:|
| Prometheus | /prometheus/prometheus.yml |
| AlertManager | /alertmanager/alertmanager.yml |
| Alert Rules | /alertmanager/alert.rules |


### Start containers using docker-compose
To start all the containers, run the following command:
```
docker-compose up -d

```

## Grafana
Once deployed, you can access Grafana by using the address http://hostname:3000 

>admin / admin will be the default username & password, it will automatically ask you to update it.

You will then need to add Prometheus as a Data Source by following this procedure:

- Click on ![Gear Icon](/images/gearicon.png) in the left menu. 
- Select Data Sources
- Click Add data source
- Select Prometheus
- Set URL to http://hostname:9090
- Set Access to: Browser
- Click "Save & Test"

To import a dashboard:
- Click on the ![Plus Icon](/images/plusicon.png) icon
- Select Import
- In the import via grafana.com, we suggest: 1860
- Click Load
- In the Prometheus section, select the Prometheus data source you just created
- Click Import


