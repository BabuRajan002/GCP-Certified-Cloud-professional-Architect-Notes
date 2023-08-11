Course Agenda:

1. Introduction
2. Designing and Planning a Cloud Solution Architecture
3. Managing and provisioning a solution infrastructure
4. Designing for security and Compliance
5. Analyzing and Optimizing Techinical and Business Processes
6. Managing Implementation and Ensuring solution and operations reliability
7. Case study preparation and your next steps


![Alt text](Images/courses-skill-badges.jpg)

What is VPC Service controls?

Using this perimeter we can lock down our GCP services similar to how firewall protects our servers.

Load Balancing:
=================
Global and Regional Load balancers:

Global:
-> External HTTP(s) Load Balancing
-> External SSL Proxy Load balancing
-> External TCP Proxy Load balancing

Regional Load Balancers:
=========================
Def: Regional load balancers are External/Internal load balancers

-> Regional External HTTP(s) Load Balancing
-> Internal HTTP(s) Load Balancing --> It's proxy based internal Layer-7 Load balancer
-> Internal TCP Proxy Load Balancing
   * Regional, private load balancer
   * RFC 1918 IP addresses
   * Its a software defined fully distributed LOad balancer
-> Internal TCP/UDP Load Balancing
-> External TCP/UDP Network Load balancing
-> External TCP Proxy load balancing

Different Deployment strategies:
================================

Blue/Green:
-----------
-> Only one version is live at a time
-> Once the green (new version) deployed and tested, when it is stable traffic will be routed.
-> There is no downtime
-> Blue version is kept for sometime for possible rollback.

Canary deployment:
------------------
-> Deploy the new version, next to the old one
-> Subset of production traffic will be sent to this new version to evaluate its performance
-> Benefit of this pattern is that you are testing it against the production traffic

A/B testing:
------------
-> It is closer to the canary testing
-> Measure the effectiveness of proposed changes
-> Canary is concerned with production performance where as A/B is more concerned with the new features.

