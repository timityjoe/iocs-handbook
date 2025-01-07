=======================
Installation - Docker
=======================

Source Code structure for IOCS
==============================

IOCS was written in Typescript (NodeJS) for high performance web
middleware. Please refer to the setting up with source code for detailed
compilation of source code to nodeJS modules.

File structures for Containers
==============================

All IOCS containers and dependencies’ configuration files are kept in
Containers folder.

Building containers for IOCS
============================

In order to build the containers for IOCS, user will first need to
create the base image from source code. To build the base image, run the
following

::

   docker  build -f ./Containers/rmf-base.Dockerfile . -t mctdis/rmf-base

To run all services for orion context broker in development mode

::

   docker compose up -d

To run all services for orion context broker in hardened mode (i.e. only
APIs are exposed to the client systems)

::

   docker compose up -f compose.prod.yaml -d

All containers are running in network rmf_development_rmf-network

Docker Containers
=================

Below is a comprehensive list of containers in this deployment along
with their port configurations and descriptions.

+------------+-------+----------+------------+-----------+-----------+
| Container  | Servi | Descript | Internal   | Exposed   | Dependenc |
| Name       | ce    | ion      | Port       | Port      | ies       |
+============+=======+==========+============+===========+===========+
| N/A        | scorp | NGSI-LD  | 9090       | 9090      | postgres  |
|            | io    | Context  |            |           |           |
|            |       | broker   |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| N/A        | postg | PostgreS | 5432       | 5432      | none      |
|            | res   | QL       |            |           |           |
|            |       | Database |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| rproxy     | nginx | Nginx    | 8889       | 9999      | scorpio,  |
|            | proxy | Reverse  |            |           | orion     |
|            |       | Proxy    |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| rmf_proxy  | proxy | RMF      | 4204       | 8003      | mongodb,  |
|            |       | Proxy    |            |           | rabbitmq, |
|            |       | Service  |            |           | redis     |
+------------+-------+----------+------------+-----------+-----------+
| N/A        | redis | Redis    | 6379       | 6379      | none      |
|            |       | Cache    |            |           |           |
|            |       | (optiona |            |           |           |
|            |       | l)       |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| rmf-mongod | mongo | MongoDB  | 27017      | 27016     | none      |
| b          | db    | Database |            |           |           |
|            |       | (optiona |            |           |           |
|            |       | l)       |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| orion      | orion | FIWARE   | 1026       | 1026      | mongodb   |
|            |       | Orion    |            |           |           |
|            |       | Context  |            |           |           |
|            |       | Broker   |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| N/A        | rabbi | RabbitMQ | 5672,      | 5672,     | none      |
|            | tmq   | Message  | 15672      | 15672     |           |
|            |       | Broker   |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| evt_mgr    | event | Event    | 4203       | 8002      | redis,    |
|            | mgr   | Manager  |            |           | mongodb,  |
|            |       | Service  |            |           | rabbitmq  |
+------------+-------+----------+------------+-----------+-----------+
| it_connect | it-co | IT       | 4201       | 8001      | redis,    |
| or         | nnect | Connecto |            |           | mongodb,  |
|            | or    | r        |            |           | rabbitmq  |
|            |       | Service  |            |           |           |
+------------+-------+----------+------------+-----------+-----------+
| rmf-swagge | rmf-s | Swagger  | 4200       | 8000      | mongodb,  |
| r          | wagge | Document |            |           | rabbitmq, |
|            | r     | ation    |            |           | orion,    |
|            |       |          |            |           | scorpio,  |
|            |       |          |            |           | it-connec |
|            |       |          |            |           | tor       |
+------------+-------+----------+------------+-----------+-----------+
| rmf-logger | rmf-l | Logging  | 4205       | 8004      | redis,    |
|            | ogger | Service  |            |           | mongodb,  |
|            |       |          |            |           | rabbitmq  |
+------------+-------+----------+------------+-----------+-----------+
| N/A        | postg | Logger   | 5431       | 5431      | none      |
|            | res-l | Database |            |           |           |
|            | ogger |          |            |           |           |
|            | s     |          |            |           |           |
+------------+-------+----------+------------+-----------+-----------+

Volume Mounts
-------------

================ ===================================================
Service          Mount Path
================ ===================================================
postgres         ``./data_volume/postgres:/var/lib/postgresql/data``
mongodb          ``./data_volume/mongodb:/data/db``
postgres-loggers ``./data_volume/logger:/var/lib/postgresql/data``
================ ===================================================

Network Configuration
---------------------

All services are connected to the ``rmf-network`` network with the
following aliases:

============ =============
Service      Network Alias
============ =============
mongodb      mongodb
orion        ngsi_v2
scorpio      ngsi_ld
rabbitmq     rabbitmq
postgres     postgres
nginx proxy  proxy
redis        redis
it-connector it_connector
rmf-swagger  swagger
eventmgr     event_mgr
rmf_proxy    rmf_proxy
rmf-logger   rmf_logger
============ =============

Database Configurations
-----------------------

PostgreSQL
~~~~~~~~~~

-  User: ngb
-  Database: ngb

MongoDB
~~~~~~~

-  Database: RMF_DATA_CONFIG
-  Application Logs DB: APPLICATION_LOGS

Web Endpoints
-------------

============== ========
Service        Endpoint
============== ========
RabbitMQ Admin /
Event Manager  /docs
Swagger        /docs
IT Connector   /docs
============== ========

Health Checks
-------------

Several services implement health checks for reliability:

-  **postgres**: Checks database readiness every 10s
-  **mongodb**: Pings admin command every 5s
-  **redis**: Checks connection using ping increment
-  **rabbitmq**: Runs diagnostics ping every 10s
-  **orion**: Checks HTTP endpoint every 10s
-  **it-connector**: Checks docs endpoint every 10s
-  **rmf-swagger**: Checks HTTP endpoint every 10s
-  **rmf-logger**: Checks docs endpoint every 10s
-  **postgres-loggers**: Checks database readiness every 10s

The development portal can be accessed via “http://localhost:8000”

::

   docker run [-p ] [-e ] --net rmf_development_rmf-network [--ip XXX.XXX.XXX.XXX] 

