============
The Digital Platform
============

The primary users of the platform are teams building or maintaining digital services. It is designed to provide them with a safe and agile self-service devops user experience. The platform is intended to scale up to large GDS digital service builds. At the same time, it is intended scale down to work well for an individual data scientist creating an `R Shiny data tool <https://shiny.rstudio.com>`_.  

The philosophy of the platform is that we can treat the people who build software as our internal users and empower them to self-service their devops needs. At the same time, the standardisation and templates used to achieve self-service automatation can embed devops best-practices. This will make our applications and services more consistent, supportable and maintainable than those of the past. 

Platform Technologies
----------

The platform supplies templates and lightweight automation with embedded best practice. These run across three best-of-breed cloud product sets that provide complementary capabilities: 

* `Visual Studio Team Services (VSTS) <https://www.visualstudio.com/team-services/>`_ is a Microsoft `Software-as-a-Service <https://en.wikipedia.org/wiki/Software_as_a_service>`_ product set used by the platform as the build and release service. VSTS has many integrations such as first-class support for GitHub. It supports deploying to many different platforms using simple "task" plug-ins  including Microsoft Azure and `Amazon AWS <https://marketplace.visualstudio.com/items?itemName=AmazonWebServices.aws-vsts-tools>`_. 

* `Openshift Container Platform (OCP) <https://www.openshift.com/container-platform/index.html>`_ is a commercially supported `Containers-as-a-Service <https://www.webopedia.com/TERM/C/caas-containers-as-a-service.html>`_ product used by the platform as the deployment and hosting service. OCP is run on DfE managed Azure `Infrastructure-as-a-Service <https://www.webopedia.com/TERM/I/IaaS.html>`_ virtual machines and networks. OCP supports a self-service model of using templates to provision containers onto a shared cluster. OCP provides developers with out-of-the-box devops best practices including container scale out, deployment patterns, high availability, A/B testing, service discovery, secret management, role-based access control and others. 

* `Microsoft Azure <https://azure.microsoft.com/en-gb/services/sql-database/>`_ is used primarily for `Database-as-a-Service <https://www.webopedia.com/TERM/C/cloud_database.html>`_ by the platform to provide SQL databases, caches, blob stores, and security key stores. As the platform is entirely Azure hosted additional services can be easily consumed such as Azure Service Bus, Azure CDN and Azure API management. The platform uses a consistent approach to handling system credentials to access any Azure service. The first team to integrate with any additional Azure service makes it consumable by all teams that use the shared platform. 

At a high-level VSTS provides services to build and release software onto the OCP plant. The OCP plant provides services to deploy, control, and keep running web applications using devops best-practice. Microsoft Azure provides stateful backing services used by web applications such as databases, caches, and stores. Both VSTS and OCP are hosted on the Microsoft Azure Cloud and are discussed in the following sections.

These product sets were chosen to best align the platform to the current DfE expertise of Microsoft cloud technologies. At the same time it introduces OCP for template driven self-service provisioning, deployment, control, and hosting of contrainerised software releases. 

Visual Studio Team Services
---------------------------

Visual Studio Team Services (VSTS) is a software development service that has good integrations with other services such as GitHub. The platform integrates with the build and release features of VSTS using some lightweight VSTS tasks that: 

* Create new team environment on the plant. 
* Deploy software releases into the plant.
* Deploy configuration as to how the software runs on the plant.
* Promote software and configuration between plant environments.

VSTS has strong auditing of release activity, role-based access control for releasing software, and strong secret management features. This allows developers to deploy software into the plant in an auditable and repeatable manner using a defined software development lifecycle. 

.. note::
    You can learn more about Visual Studio Team Services from the `Microsoft website <https://azure.microsoft.com/en-gb/services/visual-studio-team-services/>`_ and the `Build and Release <https://docs.microsoft.com/pdfstore/en-us/MSDN.team-services/live/build-release.pdf>`_ documentation. 

Openshift Container Platform
----------------------------

Openshift Container Platform (OCP) is a commercially support distribution of the OpenShift Origin open source project. OCP provides a self-service model to devops that is driven by JSON or YAML templates managed using git and simple scripting. 

    OpenShift Origin is a distribution of Kubernetes optimized for continuous application development and multi-tenant deployment. OpenShift adds developer and operations-centric tools on top of Kubernetes to enable rapid application development, easy deployment and scaling, and long-term lifecycle maintenance for small and large teams.

    -- Openshift_ 

OpenShift is built on top of `Kubernetes <https://kubernetes.io>`_ which is an open-source platform designed to automate deploying, scaling, and operating application containers. Application containers are a solution to the problem of how to get software to run reliably when moved from one computing environment to another: 

    Put simply, a container consists of an entire runtime environment: an application, plus all its dependencies, libraries and other binaries, and configuration files needed to run it, bundled into one package. By containerizing the application [services] and [their] dependencies, differences in OS distributions and underlying infrastructure are abstracted away.

    -- Cio_

.. note::
    You can read more about how OpenShift relates to Kubernates at this `levvel.io blog post <https://github.com/DFEAGILEDEVOPS/cloud-platform-docs/blob/19ebe7241f7b20857e81c4a5bfb1308951b0ae79/levvelblog.pdf>`_ reproduced with permission from Levvel, LLC (`www.levvel.io <http://www.levvel.io>`_)

Application containers are designed to package and run a single software component referred to as a software service. This supports and encourages the best practices of building applications out of components that can be individually upgraded or scaled. Kubernetes ensures that enough software services are running to support user demand. It will automatically compensate for either hardware or software failures by launching new containers on available infrastructure. 

OpenShift automates the creation of application containers from software releases. It then enables the rapid and easy deployment of them onto Kubernetes using templates and automation. Templates can capture best practices that are then easily shared between teams. This combined with automation allows teams to focus on their end-user needs freed from routine and repetitive tasks. At the same time, the plant can focus on operational concerns such as high availability.  

.. note::
    You can learn more about OpenShift from a developer and devops perspective from two free books `OpenShift for Developers: A Guild for Impatient Beginners <https://www.openshift.com/promotions/for-developers.html>`_ and `DevOps with OpenShift: Cloud Deployments Made Easy <https://www.openshift.com/promotions/devops-with-openshift.html>`_

.. _Openshift: https://github.com/openshift/origin
.. _Kubernetes1: https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/
.. _Cio: https://www.cio.com/article/2924995/software/what-are-containers-and-why-do-you-need-them.html

Dfe Platform Tools
------------------

One of the primary forces working against operational consistency and standardisation is choice. Cloud vendors want to win workload (i.e., monthly build revenue stream) from games companies, media companies, retail companies, financial services companies, mobile application companies, governments, start-ups in any and every sector or industry. Cloud vendors are chasing developer mindshare; they are trying to be the preferred platform for developers to write solutions that win them revenue. It is a very highly competitive space where new features come faster than it is reasonable for any mature organisation to evaluate and adopt them without running a full time dedicated innovation laboratory.

It is unreasonable for any one organisation to assume that any new release of an cloud technology or service is optimised for them. Typically new cloud product releases are full of new features and options that add to any every growing list. The job of standardising and automating one set of cloud features falls with each organisation. To do this an organisation needs to pick the patterns and features they use, make templates, and automate the use of those templates with wrapper scripts that enforce organisation beat practices. In a sense rather than customising technology the organisation needs to subset it; pick out the bits that match your organisations' technology choice and best practices.

The platform pilot wrote automation for the creation of VSTS projects, Git repos, and builds. It also wrote automation for creating Azure resources such as databases, caches, and key stores. VSTS tasks where then used to deployed coded based on Openshift templates. This represented the set of organisation preferences that effectively subsetted two of the core platform product sets; VSTS and Azure. The pilot also created Openshift templates to deploy a dotnet core application using the BAT alpha codebase. This automation tasks will be refined during the platform beta, and continuous improvement phases post go live.

The `dfe-platform-tools project <https://github.com/DFEAGILEDEVOPS/dfe-platform-tool>`_ hosts the templates and wrapper scripts used to automate the product platform product sets using organisation and devops/techops best practice.

Principles
----------

The primary principles of the platform are: 

* Automation, standardization and isolation provide both speed and safety
* Be open and agnostic to be able to deal with change
* Treat infrastructure as code so that it can be provisioned safely and at speed
* Keep state in managed services
* Scale down as well as up to maximise productivity

These principles and examples of how they affect the platform are outlined in `Appendix 1`_. Being explicit about the principles allows people to challenge the model and point out any deviatations from the platform principles. 

.. _`Appendix 1`: ./appendix1.html
