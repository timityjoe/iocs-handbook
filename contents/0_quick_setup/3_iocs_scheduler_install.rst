=====================================================
Installation - IOCS Robot Task Generator & Scheduler
=====================================================

1) Installation by Container
==============================

TODO

2) Installation by Source
==============================

Download the source code
````````````````````````

Clone the RMF scheduler repository into a ROS2 workspace.

.. code-block:: bash

   cd <path-to-workspace>/src
   git clone git@gitlab.com:ROSI-AP/rosi-ap_commercial/ihi/rmf2_scheduler.git \
     -b release/ihi-staging

If you need the latest changes, please use the ``release/ihi-staging`` branch.
There is also a `Github mirror`__.

__ https://github.com/open-rmf-industrial/rmf_scheduler/tree/release/ihi-staging

There are a few dependencies that must be installed from source.
Download them through ``vcstool``.

.. code-block:: bash

   cd <path-to-workspace>
   vcs import src < src/rmf2_scheduler/deps.repos

Ensure all the other dependencies are installed.

.. code-block:: bash

   cd <path-to-workspace>
   source /opt/ros/humble/setup.bash
   rosdep install --from-paths src --ignore-src --rosdistro "$ROS_DISTRO" -y


Compiling Instructions
``````````````````````

On ``Ubuntu 22.04``, with **Humble**.

.. code-block:: bash

   cd <path-to-workspace>
   source /opt/ros/humble/setup.bash
   colcon build

.. note::

   The first time when compilation occurs, some of the 3rd party dependencies
   such as `Taskflow`__, `Ortools`__ and more
   are downloaded from Github.
   Please make sure you have **an active internet connection**.

__ https://github.com/taskflow/taskflow
__ https://github.com/google/or-tools
