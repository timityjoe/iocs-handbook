IOCS Handbook 
=========================

Introduction
-----------------

IOCS Handbook is the proto handbook for RMF2.0 application on a concrete logistics example.
Significant changes have been made, to RMF1.0, that enables RMF Industrial (RMF2.0)
   - Introduction of Fiware
   - Introduction of VDA5050 MQTT


Quick Setup and Installation (Docker)
-------------------------


Quick Setup and Installation (From source)
-------------------------


Quick Setup Verification
-------------------------


Systems Design & Architecture
-------------------------

Overall Systems Design
-------------------------

IT Architecture
-------------------------
   :doc:`Systems Design - Information Technology Architecture <./contents/sys_it_design>` 

Verification & Validation - Systems Integration and Test Approach
-------------------------
   :doc:`Systems Integration and Test Approach <./contents/sys_integrations>` 



Modules
===============
Robot Task Generator
----------------------
   :doc:`Robot Task Generator <./contents/robot_task_generator>` 

Robot Task Scheduler
----------------------
   :doc:`Robot Task Scheduler <./contents/robot_task_scheduler>` 

Task Orchestrator
----------------------
   :doc:`Robot Task Generator <./contents/task_orchestrator>` 

MAPF
----------------------
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