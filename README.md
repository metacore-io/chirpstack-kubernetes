# Metacore.io ChirpStack Helm Chart alpha 0.1

*all pull request and issues welcome

also have rancher chart version, please check
https://github.com/metacore-io/metacore-charts

# ChirpStack Helm Chart Kubernetes

This repository contains a skeleton to setup the [ChirpStack](https://www.chirpstack.io)
open-source LoRaWAN Network Server stack using [Docker Compose](https://docs.docker.com/compose/).

**Note:** Please use this `docker-compose.yml` file as a starting point for testing
but keep in mind that for production usage it might need modifications. 

## Directory layout

* `values.yml`: the docker-compose file containing the services
* `templates/chirpstack*`: directory containing the ChirpStack configuration file variables, see:
    * https://www.chirpstack.io/gateway-bridge/install/config/
    * https://www.chirpstack.io/network-server/install/config/
    * https://www.chirpstack.io/application-server/install/config/
    * https://www.chirpstack.io/geolocation-server/install/config/
* `charts/postgresql/values.yaml`: directory containing PostgreSQL config and initialization scripts

## Configuration

The ChirpStack stack components components are pre-configured to work with the provided
`configmap-xxx.yml` files and defaults to the EU868 LoRaWAN band. Please take a look at configmap variables 
You can change default values by defining configmap variables in `values.yaml`.

# Data persistence

PostgreSQL and Redis data can be persisted on PVC volumes, see the `values.yml`
`volumes` definition.


**Note:** during the startup of services, it is normal to see the following errors:

* ping database error, will retry in 2s: dial tcp 172.20.0.4:5432: connect: connection refused
* ping database error, will retry in 2s: pq: the database system is starting up


After all the components have been initialized and started, you should be able
to access from the ingress endpoint.

### Add Network Server

When adding the Network Server in the ChirpStack Application Server web-interface
(see [Network Servers](https://www.chirpstack.io/application-server/use/network-servers/)),
you must enter `chirpstack-networkserver:8000` as the Network Server `hostname:IP`.
