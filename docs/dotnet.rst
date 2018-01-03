=============
ASP.NET Core
=============

    ASP.NET Core is a cross-platform, high-performance, open-source framework for building modern, cloud-based, Internet-connected applications.

    -- Microsoft_ 

.. _Microsoft: https://docs.microsoft.com/en-us/aspnet/core/

Visual Studio Team Services
---------------------------

In order to deploy to DfE Azure  code must be built into releases by Visual Studio Team Services (VSTS). VSTS then holds the system credentials to release the built artifacts into OpenShift running on DfE Azure. Release can then be controlled by the release workflow and approvals functionality of VSTS. The GDS service manual `encourage coding in the open <https://www.gov.uk/service-manual/service-standard/make-all-new-source-code-open>`_. 

Typically government digital teams code against public repositories hosted on GitHub. VSTS supports building and releasing code that is hosted on GitHub. This allows a team to host their code on GitHub and build official artifacts on VSTS that are deploy onto DfE hosted OpenShift using VSTS release workflows. You can read more about how the pilot integrates with VSTS `here </platform_technologies.html#visual-studio-team-services>`_. 

Openshift Container Platform
----------------------------

The platform uses the commercial distribution of OpenShift "RedHat OpenShift Container Platform (OCP)" that has long term support and receives security updates. You can read more about OCP `here </platform_technologies.html#openshift-container-platform>`_. 

A key benefit of using a commercially support distribution is that we recieve security updates for images and runtimes supported by OCP. This includes ASP.NET Core, Node and Ruby. This means that RedHat supplies timely security fixes for both the .Net SDK and the container image with the dependencies required to run the SDK within a Docker image. The patch history for the ``dotnet-20-rhel7`` image can be seen `on the readhat portal <https://access.redhat.com/containers/?tab=tags#/registry.access.redhat.com/dotnet/dotnet-20-rhel7>`_. 

As the platform wishes to use security patched versions of the RedHat ASP.NET Core distribution any ``Dockerfile`` within the team git repo will be ingored by the platorm. To build deployed to the platform run a ``dotnet publish`` using .Net Core SDK flags that target rhel7 such as:

:: 

    dotnet publish -r rhel.7-x64 --self-contained false --configuration $(BuildConfiguration) \ 
    --output $(build.artifactstagingdirectory) /p:PublishWithAspNetCoreTargetManifest=false

This will create a site release within ``$(build.artifactstagingdirectory)`` that can be automatically zipped up and posted into an OpenShift binray build using the ``--from-archive`` `feature <https://docs.openshift.com/container-platform/3.6/dev_guide/dev_tutorials/binary_builds.html>`_. 