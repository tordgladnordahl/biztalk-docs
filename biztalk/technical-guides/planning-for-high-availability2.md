---
title: "Planning for High Availability2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65271fd5-5294-406f-87f8-3aa394c235a2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for High Availability
High availability for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] focuses on recovering functional components that might disrupt availability in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.  
  
 To demonstrate high availability in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], you have to cause a failure and measure the product's effectiveness in recovery. A highly available [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment makes errors and failures transparent to external applications and systems, and ensures that all services continue functioning correctly with minimal disruption.  
  
 Designing a [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] deployment that provides high availability involves implementing redundancy for each functional component involved in an application integration or business process integration scenario. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] simplifies the implementation of these scenarios by conceptually separating the data from the *hosts* that process the data. A *host* is a logical container of BizTalk items, such as orchestrations, send handlers, and receive handlers. You create *host instances* and assign them to the host. A host instance is the physical representation of a host on a specific server. It is either the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] service process called BTSNTSvc.exe or another process, for example, the IIS process. So providing high availability for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] involves running multiple *host instances* and clustering the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, as follows:  
  
-   **Architecture for BizTalk Hosts**. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] lets you separate hosts and run multiple host instances to provide high availability for key functions such as receiving messages, processing orchestrations, and sending messages. These hosts do not require any additional clustering or load-balancing mechanism because [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] automatically distributes workload across multiple computers through host instances. However, hosts running the receive handlers for the HTTP and SOAP adapters require a load-balancing mechanism such as Network Load Balancing (NLB) to provide high availability, and hosts running the receive handlers for FTP, MSMQ, POP3, SQL, and SAP require a clustering mechanism to provide high availability.  
  
    > [!NOTE]  
    >  You must always cluster the SAP receive adapter to accommodate a two-phase commit scenario.  
  
-   **Architecture for BizTalk Server databases**. High-availability configuration for the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] databases typically consists of two or more [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database computers configured in an active/passive server cluster configuration. These computers share a common disk resource (such as a RAID 1+0 SCSI disk array or a storage area network) and use Windows Failover Clustering to provide backup redundancy and fault tolerance.  
  
 Another BizTalk functional component that is critical for high availability is the master secret server. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relies on this service to obtain the encryption key.  
  
 This section provides information about how to address high availability in each of these categories. Because a [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] high availability solution is built on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] and [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], make sure that you deploy these products with high availability before configuring hosts for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. The following links include information about providing high availability for these underlying products:  
  
-   **White Paper: High Availability—Always On Technologies** available at [http://go.microsoft.com/fwlink/?LinkId=156812](http://go.microsoft.com/fwlink/?LinkId=156812).  
  
-   Get more information about troubleshooting issues with Windows Server 2008 at the [Windows Server 2008 Deployment, Managing and Troubleshooting page](http://go.microsoft.com/fwlink/?LinkId=156813) (http://go.microsoft.com/fwlink/?LinkId=156813).  
  
-   Get more information about availability and scalability in Windows Server 2008 at [Availability and Scalability](http://go.microsoft.com/fwlink/?LinkId=156814) (http://go.microsoft.com/fwlink/?LinkId=156814).  
  
-   See the **High Availability** section of the [Windows Server 2008 R2 Articles and Whitepapers page](http://go.microsoft.com/fwlink/?LinkId=157760) (http://go.microsoft.com/fwlink/?LinkId=157760).  
  
## Understanding the Impact of a Component Failure  
 The following table lists the components and dependencies of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and the impact on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment if the component or dependency fails. You should consider the scope of a potential failure when deciding whether to cluster a component or dependency.  
  
|Component or dependency|Scope of failure|  
|-----------------------------|----------------------|  
|[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]|Systemwide. If [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] fails then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will be unable to process documents.|  
|Master secret server|Systemwide. If the master secret server fails then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will be unable to process documents. **Note:**  If the master secret server fails, each BizTalk server in the BizTalk group will continue to use a cached in-memory copy of the master secret until the Enterprise SSO service on that BizTalk server is restarted. If the Enterprise SSO service is restarted on the BizTalk servers, then the cached copy of the master secret is released from memory and the BizTalk servers must be able to contact the master secret server to obtain another copy of the master secret. Do not restart the Enterprise SSO service on the BizTalk server(s) in a group if the master secret server fails and you want the BizTalk server to continue processing documents.|  
|MSDTC|Server. If MSDTC fails then any component on the server that requires transaction support will fail. **Note:**  Because [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and the master secret server are dependent on MSDTC for transaction support, the scope of the failure will become system wide if the MSDTC on the SQL server or master secret server fails. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires transaction support when communicating with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and the master secret server during run-time operations.|  
|BizTalk Host instance|Server. Any components housed in a BizTalk Host instance will be unable to participate in document processing if the host instance fails.|  
|Microsoft Message Queuing (MSMQ)|Server. If MSMQ fails then any document processing that is dependent on the MSMQ service, such as the MSMQ adapter, will be halted on the server.|  
|File system|Server. If the file system fails then any document processing that is dependent on the file system, such as the File adapter, will be halted on the server.|  
  
 To be able to better manage a highly available [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system, you must have a good understanding of the BizTalk stack: [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], DC (DNS, DHCP), [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], IIS server, File server, MSMQ server, external applications. This section focuses on the high availability of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the dependent [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.  
  
## BizTalk Server High-Availability Examples  
 For sample scenarios in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that provide high availability through scaled-out tiers of hosts, see [Sample BizTalk Server High Availability Scenarios](http://go.microsoft.com/fwlink/?LinkId=156815) (http://go.microsoft.com/fwlink/?LinkId=156815).  
  
## See Also  
 [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [High Availability for Databases](../technical-guides/high-availability-for-databases.md)   
 [High Availability for the Master Secret Server](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)