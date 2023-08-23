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




