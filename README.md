# fluentd-influxdb-grafana

Ready to use fluentd-influxdb-grafana using docker-compose

## Installation
```bash
git clone https://github.com/Coac/fluentd-influxdb-grafana.git
cd fluentd-influxdb-grafana
```

## Usage
```bash
docker-compose up
```

### Fluentd
fluentd will look for json log in `logs/logs.json` and push them into influxdb.

Use the following command to push dummy data
```bash
for i in {1..100}; do echo \{\"time\":$(($(date +"%s")+$i)),\"foo\":\"foo\",\"bar\":$RANDOM\} >> logs/logs.json; done
```

### InfluxDB
The InfluxDB exposes a shared volume for the data, it uses the folder  `./data/` per default.

### Grafana
You can browse grafana using http://localhost:3000/
- Username: admin
- Password: admin

Select the influxdb datasource and use the following configuration:
- URL: http://influxdb:8086
- Database: test
- User: admin
- Password: admin
