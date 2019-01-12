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

Use the following command to push a dummy data
```bash
echo \{\"time\":$(date +"%s"),\"foo\":\"foo\",\"bar\":42\} >> logs/logs.json
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
