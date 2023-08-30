Compute Engine Machine family:
===============================

General Purpose (E2, N2, N2D, N1) - Best price-performance ratio
--> Web and Application servers, Samll-medium databases, DEV Environments

Memory Optimized (M2, M1): Ultra high memories
--> Large in-memory databases and In-memory analytics

Compute Optimized (C2): Compute intensive workloads
--> Gaming

Static IP:
==========

--> The Static IP and VM must be in the same region.
--> Can Switch the Static IP from one VM to another VM
--> Static IP remians attached even if you stop the instance
--> Billed for Static IP even though when we are not using it

Instance Template:
==================

--> CANNOT be updated (Make a change, copy an existing template and modify it)
--> It Can be used in different regions and Zones
--> There is no Cost involved for instance template

Custom Image:
=============

--> It Can be created in the below ways
    * From an instance
    * From persistent disk
    * Snapshot
    * Another image
    * File in a cloud storage

--> A Custom image can be shared across the projects

Sole Tenant:
=============
--> In case if we need a dedicated hardware we need to create a Node group under the sole tenant
--> Once created we need to use this node group name while creating our VM

VM Manager:
============
--> If we want do the OS patch management for 1000 of VMs we should this VM Manager

Instance groups:
=================

There are Two types of instance groups:
1. Managed Instance groups
2. Unmanaged instance groups

Managed Instance groups:
========================
--> Identical VMs created using a template
     Features: Auto scaling, Auto healing and managed releases

--> Unmanaged: Different configuration for VMs in same group (Does not support the above features)

Cloud Load Balancing:
======================
-> Fully distributed software defined

*** IMPORTANT ***
========================================================================================================================================================
HTTP Vs HTTPS Vs TCP vs TLS Vs UDP

Application Layer (Layer 7)  -----> HTTP HTTPS SMTP FTP
-> Make REST API calls and Send emails

Transport Layer (Layer4)  --------> TCP TLS UDP
-> Responsible for checking whether the bit and bytes are transferred properly?
-> TLS (Transport Layer Security), It ensures the security for the packets transferred over the internet.
-> UDP (User Datagram Protocol)- It gives importance to the high performance over the reliability. If OKay to lose few bytes while transferring. 
     For ex: Video streaming application

Network Layer(Layer3 ) -----------> IP 
-> Transfers bit and bytes
-> Unreliable

Remember : Most applications talk at the applcation layer. But some aplication talk at network layer directly (High performance applications)

HOWEVER applications need high performance will directly communicate at the transport layer
* Gaming applications and live video streaming use UDP

========================================================================================================================================================

Network tiers in GCP:
======================
1. Premium tier ---> Useful for Global routing
2. Standard tier ---> Forwarding rule and its external IPs are regional

Architects:
============

"It is not sufficient to get things working. We want more"

* Build Resiliency
* Increase Availability
* Increase Scalability
* Improve Performance
* Improve security

App Engine Environments:
=========================
Standard: Applications run in language specific sandboxes
-> Complete isolation from OS/Disks/Other Apps
Flexible: Application instances run within Docker containers
-> Make use of Compute Engine virtual machines
-> Support ANY runtime

App engine hierarchy:
=====================

Application: One App per project
Services: Multiple microservices or App components
Versions: Each version can run in one or more instances

Note: If we want to create App engine in multiple regions we need to have a multple projects!

How App Engine works?

-> The App engine standard environment uses the GCP's CICD tool called Cloud Build and stores the App code as a apckage in the Cloud storage.


gcloud commands:
================

-> gcloud app deploy - To deplpy the App in the Appengine
-> gcloud app services list - To lists the services list
-> gcloud app versions list - To lists the versions list
-> gcloud app instances list - To lists the instance that are part of this versions
-> gcloud app deploy --version=v2 - To deploy the second version of the app.
-> gcloud app browse - Get the link of active version of application
-> gcloud app browse --version="version-id" -> get the link of the specific version of the application
-> gcloud app deploy --version v2 --no-promote - deploy the new version wihtout automatically switching the traffic.
-> gcloud app services set-traffic splits=v3=.5,v2=.5 - instead of switching all the traffic at once we are slowly switching the traffic to the newer version and v2. 

Cloud Functions:
================

1st Gen --> First version
2nd Gen --> New version built on top of Cloud RUN and Eventarc
Key advantages:
-> Longer request timeout up to 60minutes for HTTP triggered functions
-> Larger instance size: Up to 16GiB RAM with 4vCPU
-> Concurrency up to 1000 requests per function instance
-> Multiple function revisions and traffic splitting


Cloud Run:
==========

-> Cloud Runs on top of Knative open standard
-> Fully managed serverless platform for containerized applications.

Anthos:
======

-> Run the kubernetes cluster anywhere
   Cloud, Multi cloud and On premise
-> In case if we are running our Kubenetes cluster in on-premise we can use Anthos. 
-> To deploy those Anthos clusters we can use cloud Run

IAM Role:
=========
-> A Set of permissions (to perform specific actions on specfic resources)
-> A role do not about the members its all about the permissions

Policy:
-> Defines the binding a role to a member.

Three Types of roles:

1. Basic Roles - Owner/Editor/Viewer
----------------------------------
Owner - Editor + Manage roles and permissions + Billing
Editor - Viewer + Edit actions
Viewer - Read + Only actions

2. Predefined role:
-------------------
Fine grained roles predefined and managed by google

3. Custom roles:
----------------
When predefined roles are not sufficient, you can create your own roles








