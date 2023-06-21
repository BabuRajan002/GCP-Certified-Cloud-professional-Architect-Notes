Requirements, Analysis and Design:
===================================

Useful questions that cloud Architect can be asked to design the system properly.

Who - Who are the users?
      Who are the developers?
      Who are the stakeholder?
What - What does the system do?
       What are the main features?
Why - Why is the system needed?
When - When do the users need and/or want the solution?
       When can the developers be done?
How - How will the system work?
       How many users will be there?
       How much data will be there?
       
User Story:
===========

User stories describe a feature from the  user's point of view.

Key Performance Indicators (KPI):
=================================

-> Business decision makers totally rely on this KPIs.
-> Two types of KPIs are there.

1. Business KPIs
 --> Business KPIs includes the Return on investment (ROI)
 --> Earnings before interest and taxes (EBIT)
 --> Employee turnover
 --> Customer churn
2. Software KPIs
 --> How effective the software is through, Page views
 --> User registrations
 --> Clickthroughs
 --> Checkouts

 Goal Vs KPI:
 ============

 Goal --> Outcome or result you want to achieve
 KPI ---> Metrics which indicates whether we are on track to achieve

 ![Alt text](Images/smart-kpi.jpg)

Quantitative requirements can be expressed in terms of SLIs, SLOs and SLAs:
============================================================================

SLI - Is a measurable attribute of a service. Such as latency of service, throughput.
--> SLI must be time - bounded and measurable.
--> fast response time is not measurable one, instead of HTTP GET response should be below 400ms is measurable
--> Highly available is not a measurable one, instead of percentage of successful overall requests is measurable.

SLO - Its a targeted range of values measured by SLIs ex: Average latency of a service should be less than 100ms.
SLA - Its most restrictive version of SLOs. A contract between the customers and the service providers. Providing the    compensation if the service doesn't meet the specific expectations.

 ![Alt text](Images/activity-review-SLI-and-SLO.jpg)

 ========================================================================================================================

 Microservices:
 ==============

 Twelve factor App:
 ==================

 * Maximize the portability
 * Deploy to the cloud
 * Enable continuous deployment
 * Scale easily

 1st Factor --> Code base should be tracked in Version control system.
 2nd Factor --> Declare the dependencies in the codebase, such as the package manager like Maven, Pip, NPM.
 3rd Factor --> Configs. These are environment related configs such as tokens, db username, passwords, strings,        endpoints etc.. This should not be stored in source code.
 4th Factor --> Backing services, Treat backing services as a attached resources. Such Databases, caches, queues and other services are accessed via URLs. It can be easily swapped to implement the other one.
 5th Factor --> Build, release and run. 
 6th Factor --> Processes. Execute the app as one or more stateless processes.
 7th Factor --> Export the services via port binding
 8th Factor --> Scale out. Apps are running self-contained and run in seprate processes, they scale easily by adding instances
 9th Factor --> Easy disposability, for an example if an instance is not needed, you should be able to turn it off with no side effects.
10th Factor --> Keep the dev, prod environment as similar as possible
11th Factor --> Write the log messages to standard output and aggregate all logs to a single source.
12th Factor --> Admin processes. Run the admin/management tasks as one off processes. 

REST Architecture supports loose coupling:
===========================================

REST Stands for - Representational State Transfer
-> Protocol independent 
-> Most commonly used is HTTP
-> other possible is gRPC

-> Service endpoints which are supporting REST is RESTful

-> Passing representations between services is done using standard text-bases formats which is json, HTML, XML and csv.
