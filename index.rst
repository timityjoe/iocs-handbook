IOCS Handbook  
=============================
.. video:: videos/lt_video_segment.mp4
    :nocontrols:
    :autoplay:
    :playsinline:
    :muted:
    :loop:
    :width: 100%

Introduction
----------------
IOCS Handbook is the proto handbook for RMF2.0 application on a concrete logistics example.
Significant changes have been made, to RMF1.0, that enables RMF Industrial (RMF2.0)
- Introduction of Fiware
- Introduction of VDA5050 MQTT
- Introduction of Unreal Engine 5

Quick Setup and Installation (Docker) 
------------------------------------------------

Quick Setup and Installation (From source)  
------------------------------------------------

Quick Setup Verification  
--------------------------------


IOCS Systems Design & Architecture  
=====================================
   :doc:`Systems Design - Overall Architecture <./contents/2_systems_design/sys_design>` 
   :doc:`Systems Design - Information Technology Architecture <./contents/2_systems_design/sys_it_design>` 


IOCS Systems Integration, V&V
===============================
   :doc:`Systems Integration and Test Approach <./contents/3_systems_integration/sys_integrations>`


IOCS Subsystem Modules  
=============================
Higher Guidance  
--------------------------------
   :doc:`Task Generator <./contents/4_subsystems/robot_task_generator>` 
   :doc:`Task Scheduler <./contents/4_subsystems/robot_task_scheduler>` 

Lower Guidance  
--------------------------------
   :doc:`Task Orchestrator <./contents/4_subsystems/task_orchestrator>` 

IOCS Services  
----------------
   :doc:`Multi Agent Path Finder <./contents/4_subsystems/mapf>` 


Content
-------
.. toctree::
   :maxdepth: 2
   :caption: IOCS Systems Design
   :hidden:

   contents/2_systems_design/sys_design
   contents/2_systems_design/sys_it_design

.. toctree::
   :maxdepth: 2
   :caption: IOCS Systems Integration
   :hidden:

   contents/3_systems_integration/sys_integrations

.. toctree::
   :maxdepth: 2
   :caption: IOCS Subsystems
   :hidden:

   contents/4_subsystems/robot_task_generator
   contents/4_subsystems/robot_task_scheduler
   contents/4_subsystems/task_orchestrator
   contents/4_subsystems/mapf

.. toctree::
   :maxdepth: 2
   :caption: About Developer
   :hidden:
   
   developer/contribution
   developer/release
   developer/changelog