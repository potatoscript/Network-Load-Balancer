# Network-Load-Balancer

NLBは「Network Load Balancer（ネットワークロードバランサー）」の略で、ネットワークトラフィックを複数のサーバーに均等に分散させるための装置やソフトウェアのことです。これにより、特定のサーバーに過度の負荷がかかるのを防ぎ、システム全体のパフォーマンスと可用性を向上させることができます。
<details>
  <summary>Click to continue（続きを読む）...</summary>
  <br>
NLBが必要な理由は以下の通りです：

1. **負荷分散**: ネットワークトラフィックを複数のサーバーに分散させることで、特定のサーバーに過度の負荷がかかるのを防ぎます。これにより、システム全体のパフォーマンスが向上します。

2. **高可用性**: NLBを使用することで、1台のサーバーが故障しても他のサーバーがトラフィックを引き継ぐことができるため、サービスの継続性が確保されます。

3. **スケーラビリティ**: システムの需要が増加した場合、追加のサーバーを容易に導入し、NLBに追加することで、システム全体の処理能力を拡張できます。

4. **管理の容易さ**: NLBを使用することで、サーバーのメンテナンスやアップデートを行う際に、特定のサーバーへのトラフィックを停止し、他のサーバーで処理を継続することができます。これにより、ダウンタイムを最小限に抑えることができます。

具体的なコマンド例としては、Windows Server環境でNLB機能をインストールするために、以下のPowerShellコマンドを使用します：

```powershell
Install-WindowsFeature -name NLB -IncludeManagementTools
```

このコマンドにより、NLB機能とその管理ツールがWindows Serverにインストールされ、NLBクラスターの設定と管理が可能になります。
</details>

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Database Server](#database-server)

## Introduction 
[back](#table-of-contents)

A network load balancer (NLB) is a device or software application that efficiently distributes incoming network traffic across multiple servers or backend resources. Its primary purpose is to enhance the availability and reliability of applications and websites by ensuring that no single server becomes overwhelmed with traffic.
<details>
  <summary>Click to continue（続きを読む）...</summary>
  <br>
Here are some key features and characteristics of network load balancers:

1. **Traffic Distribution**: NLBs distribute incoming network traffic across multiple servers or resources based on predefined rules or algorithms. This helps in optimizing resource utilization and improving response times for clients.

2. **Load Balancing Algorithms**: They employ various algorithms such as round-robin, least connections, IP hash, or weighted round-robin to distribute traffic efficiently. These algorithms consider factors like server health, response time, and current load when making distribution decisions.

3. **Scalability**: NLBs are designed to scale horizontally by adding more servers or backend resources to handle increasing traffic demands. They can dynamically adjust to changes in workload without disrupting ongoing operations.

4. **High Availability**: NLBs enhance the availability of applications by providing failover capabilities. If one server fails or becomes unavailable, the load balancer redirects traffic to other healthy servers, ensuring uninterrupted service for clients.

5. **Health Checks**: NLBs continuously monitor the health and availability of backend servers by sending periodic health checks. If a server is detected as unhealthy, the load balancer stops routing traffic to it until it becomes healthy again.

6. **SSL Termination**: Many NLBs offer SSL termination, allowing them to offload SSL encryption and decryption tasks from backend servers. This improves performance and simplifies management of SSL certificates.
</details>

Overall, network load balancers play a crucial role in optimizing the performance, reliability, and scalability of modern web applications and services by efficiently distributing incoming traffic across multiple servers or resources.

## Installation 
[back](#table-of-contents)

1. **Install your web application on one IIS server (let's call it Server A)**: This is where your web application is initially deployed and running.

2. **Create a cluster at Server A**: In a Windows Server environment, you can create a server cluster using technologies like Windows Server Failover Clustering (WSFC). This cluster groups Server A with another server (Server B) to provide high availability and fault tolerance.
<details>
  <summary>Click to continue（続きを読む）...</summary>
  <br>
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB01.png?raw=true" />
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB02.png?raw=true" />
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB03.png?raw=true" />
</details>
Or you can just use PowerShell to create a cluster on the server, as shown in the diagram below.
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB04.png?raw=true" />

3. **Set up a network load balancer (NLB) on Server A**: You configure the NLB to distribute incoming traffic between Server A and Server B. The NLB monitors the health of both servers.
<details>
  <summary>Click to continue（続きを読む）...</summary>
  <br>
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB05.png?raw=true" />
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB06.png?raw=true" />
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB07.png?raw=true" />
</details>

4. **Register Server B in the Server A cluster**: Server B is part of the cluster, so it's aware of the resources and configurations defined in the cluster.
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB08.png?raw=true" />
If Server A goes down or becomes unavailable:

- The NLB detects the failure or unavailability of Server A through health checks.
- Traffic is automatically redirected to Server B by the NLB.
- Since Server B is part of the cluster, it's already configured to handle the web application workload and can seamlessly take over the traffic.

Your web application will automatically run on Server B when Server A is down, thanks to the combination of server clustering and network load balancing. 

This setup provides high availability and ensures uninterrupted access to your web application for users.

## Database Server 
[back](#table-of-contents)

The database is often installed on a separate server (or servers) that is independent of the web servers (Server A and Server B). This ensures that the database remains accessible even if one of the web servers goes down.

Here's how it usually works:

1. **Database Server (Server C)**: This server hosts the database management system (such as MySQL, SQL Server, PostgreSQL, etc.) and the actual database where your application data is stored. It is designed to handle database operations efficiently and reliably.

2. **Connection from Web Servers**: Both Server A and Server B connect to the Database Server (Server C) to retrieve and store data. They use connection strings or other configuration settings to establish connections to the database.

3. **High Availability for the Database**: Similar to the web servers, the Database Server can also be configured for high availability and fault tolerance. This can be achieved through technologies like database clustering, replication, or failover solutions provided by the database management system.

4. **Database Failover**: If the primary Database Server (Server C) becomes unavailable, the failover mechanism ensures that a secondary database server takes over to provide continued access to the database. This ensures that your application can continue functioning even if one of the database servers goes down.

By separating the database from the web servers and implementing high availability solutions for both, you can ensure that your entire application stack remains resilient and available to users even in the event of hardware failures, software issues, or maintenance activities.
