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


