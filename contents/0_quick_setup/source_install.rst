=======
Source Code structure for IOCS
==============================

IOCS was written in Typescript (NodeJS) for high performance web
middleware. Please refer to the setting up with source code for detailed
compilation of source code to nodeJS modules.

File structure
--------------

The source codes are grouped in modules and organized based on its
functionality. Following demonstrate the file structure of the modules

1)  DriverBaseClasses - The standardized of the database abstraction
    layer and abstraction for the event handler. It defined both the
    functionality the database connectivity and event handling
    (e.g. MQTT and AMQP handler) for all IOCS services.
2)  DatabaseDrivers - Implementation of the database abstraction layer.
    example of implementation for Postgres, SQL Server and etc.
3)  EventDriver - Implementation of the Event Handler. example of
    implementation for MQTT and RabbitMQ.
4)  DataConnectors - Database Manager that manage database connection
    instance and provide data exchange services from all database
    connections created by (2). The module also manages data models and
    data transformation pipelines from raw data to the harmonized data
    using IOCS data models registry.
5)  EventManager - Manages all event services such as RabbitMQ and MQTT
    services. It also provides functionality for broadcasting of events
    to all IOCS sub-services.
6)  RmfNodeJsWebApp - Application template for all IOCS services.
7)  OrionBroker - It manages protocol transformation. (for example, from
    simple JOSN to NGSI format and vice-versa).
8)  DataLoggers - Data Sink services to stored data to databases.
9)  SharedLibrary - Utility class for IOCS.
10) Applications - All IOCS services application service entry points
11) FiwareSwagger - Swagger generators for all IOCS services.

All IOCS internal configurations will be kept in “.env” files.

System Requirement
------------------

The source code required nodejs v 18.0 and above and tested on v20.0.
For running without containers, the following services are required.
(Services can be local services or remote services) 1) PostGis
(variation from Postgres) [https://postgis.net/] 2) RabbitMQ services
[https://github.com/rabbitmq/rabbitmq-website] 3) Scorpio Context broker
[https://github.com/ScorpioBroker/ScorpioBroker] 4) Fiware Orion Context
broker (optional) [https://fiware-orion.readthedocs.io/en/master/]

Building of all services with source code (to NodeJS)
-----------------------------------------------------

To set up the build environment for IOCS

::

   npm install -dev
   or 
   npm install -include=dev 

To install all dependencies for IOCS

::

   npm run install:dev

To build application sequentially (for build debugging purpose)

::

   npm run build:dev

To build the server side services for IOCS (without swagger services)

::

   npm run build:q

To build all services

::

   npm run build

Running of application
----------------------

1. Database Connectivity and Data Model Service
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Application services delivering functionality for Daabase Manager [4]
which manages database connections and data models.

Environment variable *PORT* should be set to 4201

::

   npm run start:v1

2. System Event Service
~~~~~~~~~~~~~~~~~~~~~~~

Application services listening to the event bus. allowing data from
Event bus to come into IOCS. and also provides interfaces to broadcast
data events to all services connected to IOCS.

Environment variable *PORT* should be set to 4203

::

   npm run start:event

3. IOCS Proxy Service
~~~~~~~~~~~~~~~~~~~~~

Application services define the data process flow and direct data to
IOCS with configured data models.

Environment variable *PORT* should be set to 4204

::

   npm run start:proxy
