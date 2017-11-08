====================
Platform Technlogies
====================

The platform comprises of two major elements: 

* `Visual Studio Team Servicesm (VSTS) <https://www.visualstudio.com/team-services/>`_ is used by the platform as the build and release service.  

* `Openshift Container Platform (OCP) <https://www.openshift.com/container-platform/index.html>`_ is used by the platform to deploy and run released software. 

At a high level VSTS provides platform services to build and release software which runs on the OpenShift plant. Both VSTS and OCP are hosted within the Microsoft Azure Cloud and are discussed in the following sections.   

Visual Studio Team Services
---------------------------

Visual Studio Team Services (VSTS) is a software development service. The platform integrates with the build and release features of VSTS. This allows developers to deploy software into the plant in an auditable and repeatable manner using a defined software development lifecycle. 

The platform will supply a number of VSTS tasks (or compatible components) that will: 

* Deploy software releases into the plant.
* Deploy configuration as to how the software runs on the plant.
* Promote software and configuration between plant environments.

In the strictest sence the platform is agnostic as to the software development live cycle orchastrated by VSTS. In practice the platform team will supply templates as to how VSTS builds software that is to be released for testing. Platform templates and automation combined with role based access controls can then both define and enforce software standards. Active Directory will be used for authentication and group membership to support access controls across the platform. 

Openshift Container Platform
----------------------------

Openshift Container Platform (OCP) is a commercially support distribution of the OpenShift Origin open source project: 

    OpenShift Origin is a distribution of Kubernetes optimized for continuous application development and multi-tenant deployment. OpenShift adds developer and operations-centric tools on top of Kubernetes to enable rapid application development, easy deployment and scaling, and long-term lifecycle maintenance for small and large teams.

    -- Openshift_ 

Kubernetes is an open-source platform designed to automate deploying, scaling, and operating application containers. Application containers are a solution to the problem of how to get software to run reliably when moved from one computing environment to another: 

    Put simply, a container consists of an entire runtime environment: an application, plus all its dependencies, libraries and other binaries, and configuration files needed to run it, bundled into one package. By containerizing the application platform and its dependencies, differences in OS distributions and underlying infrastructure are abstracted away.

    -- Cio_

Application containers are designed to package and run a single software component referred to as software services. This supports and encourages the best practices of building applications out of components that can be individually upgraded or scaled. Kubernetes ensures that enough software services are running to support user demand and will automatically compensate for either hardware or software failures. 

OpenShift automates the creation of application containers from software releases. It then enables rapid and easy deployment through automation and templates. The templates and automation can be shared between teams. This frees up a team to focus on the end user needs. At the same time automation and templates can be aligned to best practice. The underlying plant can focus on operational concerns such as high availablity and is agnostic to the specifics of the software services running within the platform.  

.. _Openshift: https://github.com/openshift/origin
.. _Kubernetes1: https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/
.. _Cio: https://www.cio.com/article/2924995/software/what-are-containers-and-why-do-you-need-them.html
