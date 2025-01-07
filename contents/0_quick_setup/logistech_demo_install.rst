=======================
Installation - Logistech Demo
=======================

This guide outlines how to install and configure the Logis-Tech UE5 Simulation, integrated with the IOCS (Context Broker), Task Orchestrator, Templated Action Nodes, and Dashboard GUI.

Prerequisites
------------------

Before starting, ensure the following:

Operating System: Ubuntu 22.04 or a compatible Linux distribution.

Required Tools:

- Docker

    Install `docker <https://docs.docker.com/engine/install/ubuntu/>`_

- tmux and tmuxinator

    a. Install tmuxinator:

    .. code-block:: bash

        sudo apt install tmux
        sudo gem install tmuxinator

- MongoDB
  
    .. code-block:: bash

        pip install pymongo
  
- Node.js, npm, and pnpm

   Check if Node.js is installed:    

   .. code-block:: bash

        node -v

   If not installed, Go to the Node.js official website.

   Visit the `Node.js download page <https://nodejs.org/>`_

   Download the latest LTS version suitable for your operating system.

   Run the installer and follow the instructions. Make sure to include the installation of `npm`.

   
   Verify the installation, run:
   
   .. code-block:: bash

      node -v

   Install pnpm,  a fast, disk space-efficient package manager
   
   .. code-block:: bash

      sudo npm install -g pnpm

   Verify the installation with:
   
   .. code-block:: bash

      pnpm -v

- Python 3 and pip

Module Installation
--------------------

1. Install Dependencies for the RMF 2 Task orchestrator

   .. code-block:: bash

     cd **workspace**/src
     vcs import . < rmf2_task_orchestrator/dep.repos 
     rosdep update
     rosdep install --from-paths src --ignore-src -r -y
     colcon build


2. Set Up the Context Broker (IOCS)

   Clone the rmf2_broker repository and bring up the environment using Docker Compose:

   .. code-block:: bash

     cd model-20240830-1321
     sudo docker compose -f compose.dev.yaml up -d

   Register Data model via the `IOCS GUI <http://localhost:8000/proxy-server>`_

   1. Scroll down to default and press on **GET /context/sink** to see the available data sinks

   2. Go to **Data Entity DataTypePipeline** and use the **POST /context/config** to add the **RMF Task Data model**

    .. code-block:: bash

       {
          "id": "Task",
          "sink": [
          "ngsi-v2",
          "ngsi-ld",
          "system_event",
          "logger"        
          ],
          "context": [
          ]
       }

  3. Add the **RMF Task Status Data Model**

   .. code-block:: bash

     {
        "id": "TaskStatus",
        "sink": [
        "ngsi-v2",
        "ngsi-ld",
        "system_event",
        "logger"        
        ],
        "context": [
        ]
    }

  4. Add the **RMF Schedule Data Model**

   .. code-block:: bash

     {
        "id": "Schedule",
        "sink": [
        "ngsi-v2",
        "ngsi-ld",
        "system_event",
        "logger"        
        ],
        "context": [
        ]
    }

3. Setup Tumuxinator

   Copy the tmux config file to the correct directory:

   .. code-block:: bash

     scp ~/IHI_LOGISTECH_UE5/ihi_logistech.yml ~/.config/tmuxinator

4.  Install the GUI

   .. code-block:: bash

     cd ihi_dashboard
     pnpm install

Usage
--------

1. Set Up the Context Broker (IOCS)

   .. code-block:: bash

    cd ~/IHI_LOGISTECH_UE5/model-20240830-1321
    sudo docker compose -f compose.dev.yaml up -d

   To turn off the context broker
   
   .. code-block:: bash

    sudo docker compose -f compose.dev.yaml down

2. Start the GUI

   Navigate to the project directory:
  
   .. code-block:: bash

    cd ~/IHI_LOGISTECH_UE5/ihi_dashboard
    pnpm start

3. Setup GUI Interface to UE5 and Task Orchestrator
  
   .. code-block:: bash

    cd ~/IHI_LOGISTECH_UE5/
    python3 dashboard_interface.py

4. Start the Simulation

   - Go to the GUI page at http://localhost:3000/#/admin/operations.

   - Click the Start Simulation button.

   Optional: If the simulation is lagging, press the "PgUp" key and then "PgDn" to resume smooth operation.

5. Send Work Orders
   
   On the same GUI page, click Start Send Task.

6. To End the Simulation
