# Solar Monitoring Stack

The aim of this project is to simplify the setup and configuration of monitoring a SunSpec compatible solar system.

## Prerequisites

### Software ###

Git (optional) - https://git-scm.com/downloads

Docker Compose - https://docs.docker.com/compose/install/

### Inverter configuration ###

Your inverter needs to be configured to have MODBUS TCP enabled.

For SolarEdge Inverters, refer to https://www.solaredge.com/sites/default/files/sunspec-implementation-technical-note.pdf

## Usage

Clone repository:
* `git clone --single-branch --branch master https://github.com/jsloane/solar-monitoring-stack.git`

To build and start containers:
* `docker-compose up -d --build`

To stop containers
* `docker-compose down`

## Configuration

### InfluxDB
Access at http://localhost:8086/

Create organisation and 2 buckets with names: `data-realtime` and `data-historical`.

Create or use the existing token for Node Red & Grafana configuration.

### Node Red
Access at http://localhost:8880/
#### Configure SunSpec Modbus node
Set 'Solar Edge MODBUS' hostname/IP address and port, and enable flow.

Set InfluxDB Token and Organisation on InfluxDB flows.

Deploy changes.

### Grafana
Access at http://localhost:3000/ and login with username: `admin`, password: `admin`.

#### Configure InfluxDB data source
Change query language to: `Flux`, enter organisaiton name and token.

## Screenshots

### Grafana
![Grafana](/docs/grafana.png?raw=true)

### Node-RED
![Node-RED](/docs/nodered.png?raw=true)

## TODO

Save nodered data elsewhere.

Preconfigure influxdb - pending https://github.com/influxdata/influxdb/pull/17946

Preconfigure grafana datasource
