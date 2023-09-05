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

Service accounts:
=================

ACL - Defines who access to your buckets and objects, as well as what level of access they have

How is this differ from IAM?
-> IAM permissions applies all the objects present in the bucket
ACL
-> Can be used to customized specific accesses to different objects.

Two Types of access in Cloud storage:
=====================================

Uniform - Apply the IAM permissions to the bucket level , NO ACls enabled
Fine grained - No bucket level permission and ACLs enabled.

Cloud Storage - Signed URL:
===========================

-> When we want to allow a user limited time access to your objects we can go with the signed URLs.
-> User do NOT need Google accounts

How to create a Signed URL?
1. Create a key (User Managed Key) for the service account/user with the desired permissions
2. create a signed URL with the key:
    * gsutil signurl -d 10m key gs://BUCKET_NAME/OBJECT_PATH

How do we measure how quickly we can recover from failure?
-> RPO - (Recovery Point Objective): Max acceptable period of data loss
-> RTO - (Recovery Time Objective): Max acceptable downtime

CloudSQL Best practices:
=========================
* Use cloudSQL proxy:
 -> Securely connect to the cloudSQL instances using this cloud-sql-proxy from the apps (App engine, Cloud Functions,
 Cloud RUN and GKE)
* Understand the scalability
  -> Enable HA configuration for HA

* CloudSQL does cannot scale horizontally for writes

NoSQL Databases:
=================

* Firestore Database:
   -> Native mode - Advanced mode 
   -> Datastore mode - Good for old datastores

Collection:
-> Group of documents

Document:
-> A document contains the actual data
-> Inside a document we can add another collection 

Collection ---> Documents ----> Collection

Collection contains documents and document contains collections.

Use cases: 
i) Recommended for storing the things like user profiles
ii) Index for objects stored in the cloud storage
    -> Allow the users to upload their profile pics in the cloud storage
    -> Enable the quick search by storing the metadata (like ids and cloud storage bucket, object details) in the cloud datastore.

Cloud BigTable:
===============

* Peta byte scale, wide column database NoSQL DB (Hbase API compatible).
* Designed for huge volumes of analytical and ops data
* IOT Streams, Analytics, Time series data etc
* Not serverless, we need to create a server instance (Use SSD and HDD).
* Use cloud dataflow to export the data from Bigtable to cloud storage
* Cloud Bigtable is a key/value store
* Each table has ONLY ONE index, the row key

Networking in GCP:
==================

* VPC is a Global resource, Subnets are tied with one or more regions.
* LOad balancers are accessible from internet (Public resources)

Modes:
- Auto mode - Subnets will be created in every region
- Custom mode - Allows us to create the subnets to the specifc regions we want.

*** Important: Auto mode network can be converted into custom mode network, but the reverse is not possible ***

Enable Private access when you create a Subnet inside the VPC

-> Allows the VM to coonnect to Google APIs using private IPs

*** Note: Instances created in Custom network will not talk to the instances created in the default network. ***

Firwall Rules:
===============
-> Stateful - By default if the incoming traffic is allowed the outgoing traffic is also allowed. 
-> Each firewall rule has priority (0-65535) assigned to it
-> 0 highest priority. 65535 has least priority
-> Default implied rule with the lowest priority 65535
   * Allow all egress 
   * deny all ingress
   * default rules can't be deleted
   * you can override the default rules by defining new rules with priority between 0-65534
-> Default VPC has 4 additional rules with priority 65534
   * Allow incoming traffic from VM instances in same network (default-allow-internal)
   * Allow incoming TCP traffic on port 22 SSH default-allow-ssh
   * Allow incoming TCP traffic 3389 RDP default-allow-rdp
   * Allow incoming ICMP from any source on the network default-allow-icmp

*** Note: By default all the egress traffic from the VM instances is allowed ***

Subnets:
========

4 IP addresses reserved

-> 1st IP - Network addr
-> 2nd IP - Gateway addr
-> 3rd IP - second to Last and last addresses reserved for broadcase addr

Internal and External IP addresses:
===================================

internal IP - Assigned from the IP ranges from the VPC subnet
external IP - external IP will be assigned either from default pool or from it canbe reserved

-> VM's OS doesn't know about the external IP. IP mapping will be taken care by VPC
-> Each instance has a metadata server 169.254.169.254 
-> Name resolution is handled by internal DNS server

Cloud Trace:
============

-> Trace the requests across multiple micro-services
-> Trace the requests across multiple Google services

Find out:
=========
* How long does a service take to handle requests.?
* Whats the average latency?
* How are we doing the over a time period?

Cloud Debugger:
===============
* Captures the state of a running application
* Inspect the state of the application directly in the GCP environment
* Take snapshots of variables and call stack

Cloud Profiler:
===============

-> To identify the performance bottlenecks in production
-> Continuously gathers CPU and Memory usage from production systems

Two Major components:
=====================
-> Profiling agent (Collects the profiling info)
-> Profiler interface (visualization)

Error reporting:
================




















