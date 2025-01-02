IOCS Handbook  
=============================

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

   :doc:`Systems Design - Overall Architecture <./contents/sys_design>` 
   :doc:`Systems Design - Information Technology Architecture <./contents/sys_it_design>` 
   :doc:`Systems Integration and Test Approach <./contents/sys_integrations>` 



Modules  
=============================

Higher Guidance  
--------------------------------
   :doc:`Task Generator <./contents/robot_task_generator>` 
   :doc:`Task Scheduler <./contents/robot_task_scheduler>` 

Lower Guidance  
--------------------------------
   :doc:`Task Orchestrator <./contents/task_orchestrator>` 

Services  
----------------
   :doc:`Multi Agent Path Finder <./contents/mapf>` 


.. toctree::
   :maxdepth: 2
   :caption: IOCS Application Guide

   contents/sys_design
   contents/sys_it_design
   contents/sys_integrations
   contents/robot_task_generator
   contents/robot_task_scheduler
   contents/task_orchestrator
   contents/mapf

   developer/contribution
   developer/release
   developer/changelog