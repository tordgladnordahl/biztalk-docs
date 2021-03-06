---
title: "Managing Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [orchestrations]"
  - "managing [orchestrations], about managing orchestrations"
  - "orchestrations, managing"
ms.assetid: 2553eec3-b863-45fb-90af-7eddcfa7add7
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Orchestrations
This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage orchestrations. An orchestration is an executable business process. For background information about orchestrations, see [Orchestrations](../core/orchestrations.md).  
  
 Orchestrations are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies. You cannot add an orchestration to an application individually; an orchestration is added to an application as follows:  
  
-   When you add a BizTalk assembly containing an orchestration to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
-   When you import an .msi file into an application that includes a BizTalk assembly containing an orchestration, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
-   When a developer deploys into an application an assembly containing an orchestration from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
 You use the administration console to perform the following actions, as described in this section:  
  
-   Configure bindings for the orchestration by binding the orchestration to the appropriate send and receive ports and host, or remove these bindings from the orchestration.  
  
-   Configure message tracking for the orchestration.  
  
-   View instance information for the orchestration.  
  
-   Enlist the orchestration to the appropriate host or unenlist the orchestration from the host.  
  
-   Start or stop the orchestration so that it starts or stops processing messages.  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see [WMI Class Reference](../core/wmi-class-reference.md).  
  
> [!NOTE]
>  The developer uses Orchestration Designer to create orchestrations, as described in [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md). The developer can manage orchestrations during the development process by using the administration console, as described in this section.  
  
## In This Section  
  
-   [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md)  
  
-   [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md)  
  
-   [How to Configure Tracking for an Orchestration](../core/how-to-configure-tracking-for-an-orchestration.md)  
  
-   [How to View Instance Information for an Orchestration](../core/how-to-view-instance-information-for-an-orchestration.md)  
  
-   [How to Remove an Orchestration from an Application](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md)  
  
-   [How to Unenlist an Orchestration](../core/how-to-unenlist-an-orchestration.md)  
  
-   [How to Start an Orchestration](../core/how-to-start-an-orchestration.md)  
  
-   [How to Stop an Orchestration](../core/how-to-stop-an-orchestration.md)  
  
-   [How to Suspend, Resume, and Terminate Orchestration Instances](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)  
  
-   [How to Upgrade an Orchestration](../core/how-to-upgrade-an-orchestration.md)