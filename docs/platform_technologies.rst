====================
Platform Technlogies
====================

The platform comprises of two major elements: 

* `Visual Studio Team Servicesm (VSTS) <https://www.visualstudio.com/team-services/>`_ is used by the platform as the build and release service.  

* `Openshift Container Platform (OpenShift) <https://www.openshift.com/container-platform/index.html>`_ is used by the platform to deploy and run released software. 

At a high level VSTS provides services to develop software which run on the OpenShift plant. Both elements will delegate authentication (and aspects of authorsiation) to Active Directory. Both elements are hosted within the Microsoft Azure Cloud and are discussed in the following sections.   

Visual Studio Team Services
---------------------------

VSTS is a hosted software development service. The platform integrates with the build and release features of VSTS. This allows an organisation to deploy software into the plant in an auditable and repeatable manner driven by a defined software development lifecycle. The platform will supply a number of VSTS compatible tasks or components that will: 

* Deploy software releases onto the test plant.
* Deploy configuration as to how the software runs on the plant.
* Promote software releases and configuration between plant environments.

In the strictest sence the platform is agnostic as to the software development live cycle. With full access to VSTS a team can reorder tasks to create any arbitrary software development life cycle. In practice templates, automation, standardisation and role based access controls within VSTS can be used to enforce software standards. 

Openshift Container Platform
----------------------------

Openshift Container Platform is a commercially support distribution of the OpenShift Origin opensource project. 