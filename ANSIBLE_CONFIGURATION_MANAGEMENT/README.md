# Ansible Configuration management(Automation)
---
Configuration management is a process for maintaining a desired state of IT systems and components. It helps ensure that a system consistently performs as expected throughout its lifecycle.
System administrators can use configuration management tools to set up an IT system, such as a server or workstation, then build and maintain other servers and workstations with the same settings. They can also use configuration assessments and drift analyses to continuously identify systems that have strayed from the desired state and need to be updated, reconfigured, or patched.
As a part of IT Service Management (ITSM) process, configuration management databases (CMDBs) track individual configuration items (CIs): any asset or component involved in the delivery of IT services. CMDBs store information about a CI’s attributes, dependencies, and changes to its configrration over time—enabling IT teams to map and maintain the relationships that tie CIs together.

---
## Ansible Client as a Jump Server (Bastion Host)
A Jump Server (sometimes also referred as Bastion Host) is an intermediary server through which access to internal network can be provided. If you think about the current architecture you are working on, ideally, the webservers would be inside a secured network which cannot be reached directly from the Internet. That means, even DevOps engineers cannot SSH into the Web servers directly and can only access it through a Jump Server - it provides better security and reduces attack surface.


#### In this Task we'll project we'll configure ansible client to serve as jump server/Bastion Host
#### And also Create a simple Ansible playbook to automate servers configuration(s)