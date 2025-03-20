# 🖥️ Network Load Balancer (NLB)

Imagine you are organizing a big party 🥳, and you want everyone to have fun, but you know that if one person tries to do everything—like greeting everyone, handing out snacks, and playing music—it’s going to be too much for them. Instead, you decide to divide the tasks among several people so that no one gets too tired or overwhelmed. The *Network Load Balancer (NLB)* does something similar but for websites and apps! It helps to divide the work between different computers (called servers), making sure no single server gets overloaded.

Let’s take a fun journey to understand how NLB works!

---

## 🌐 What is a Network Load Balancer?

A **Network Load Balancer (NLB)** is like a smart helper at your party who stands at the door and makes sure everyone gets to the right person for their snacks and fun! 🥤🍿 It helps by sending the party guests (internet traffic) to different people (servers) so that no one person has to do all the work. This keeps everything running smoothly and ensures everyone has a great time!

### Key Points:
1. **Spreads Out the Traffic**: Just like at a party, NLB ensures that the traffic coming to your website is spread out to different servers.
2. **Makes Sure Everything Works Smoothly**: It makes sure no one server gets too busy or crashes (like the tired party host).
3. **Keeps Things Running if Something Breaks**: If one of your servers fails, the NLB will automatically send traffic to other healthy servers—just like making sure the snacks keep flowing even if one person runs out of snacks!

---

## 💻 How Does NLB Work?

Let’s imagine a situation:

- You have 2 servers: Server A and Server B, and they both serve your website.
- Server A handles some traffic, but it starts getting really busy. Uh-oh! Server B jumps in and helps out by handling some of the traffic.
- **What happens if Server A crashes?** Don’t worry! The NLB will quickly send all traffic to Server B. It's like having a backup plan for your party!

### NLB's Magic Tricks:
1. **Round-robin**: Imagine you have 10 people at your party, and you want to give snacks to each person one by one. NLB uses this method, giving traffic evenly to all servers, like going around the party and offering snacks to everyone in turn.
2. **Least Connections**: This method is like choosing the person with the least amount of work to handle the next guest. If one server is already handling a lot, the NLB sends new traffic to the server with the least connections.
3. **Health Checks**: NLB keeps checking if servers are healthy (like checking if someone is feeling okay at the party). If a server is too tired, the NLB will stop sending traffic to it until it’s ready to help again.

---

## 📲 NLB Step-by-Step Setup

Let’s say we are setting up a simple NLB for a website. Don’t worry, I’ll guide you through it like a game!

### Step 1: Install Your Website on Server A
First, you put your website on **Server A**. This is where your website lives, just like your party’s main host. 🏠

### Step 2: Create a Cluster
Now, imagine you're adding **Server B** to the team! 👫 Server A and Server B become a team (cluster), and they work together to serve your website.

- In the world of computers, we use something called **Windows Server Failover Clustering** to create the team.
- When both servers work together, they can handle more traffic and ensure that the website never goes down!

### Step 3: Set Up the Load Balancer
Now that we have our two servers, we use the **NLB** to decide how to divide the traffic between them. It’s like having a helper who decides who will handle which guest at the party.

### Step 4: Register Server B
Next, we make sure Server B is part of the cluster, just like welcoming a new party guest! Server B is ready to help and can take over if Server A gets too tired or fails.

---

## 💥 What Happens if Something Breaks?

Imagine during your party, something happens and the music stops (Server A fails). But no need to panic! The NLB will quickly switch over to Server B, making sure the party (your website) keeps going smoothly! 🎶💃

---

## 🗄️ Database Server (Behind the Scenes)

Your website doesn’t just need servers to handle traffic—it also needs a place to store all the information (like party details, snack orders, etc.). This is done by the **Database Server (Server C)**.

### How it Works:
1. **Database Server (Server C)**: This server stores all the important data for your website (like names, emails, and pictures). It’s like the party’s secret storage room! 📦
2. **Web Servers (Server A & B)**: These servers (our party hosts) connect to Server C to fetch and store data. Just like party hosts going to the storage room to grab snacks!
3. **High Availability**: If Server C (the storage room) has an issue, there is a backup system ready to help, making sure your website can keep fetching and storing data.

---

## 🏅 Why NLB is Awesome

1. **Keeps Your Website Running Smoothly**: Like having many people helping out at your party, NLB makes sure your website can handle lots of visitors.
2. **Backup Plan**: If one server breaks, NLB automatically sends traffic to the other, just like a backup plan for the party.
3. **Scalable**: If your website gets super popular and you need more servers, NLB makes it easy to add them to the team!

---

## 🎉 Wrapping It Up

So, imagine you're hosting the coolest party ever, and NLB is like the best helper, making sure everything runs smoothly, spreading out the work, and stepping in when something goes wrong. With NLB, your website (the party) can handle tons of guests (traffic) and keep things fun and easy!

---

### 🖼️ Icons and Images

Here are some pictures that help explain how NLB works:

![Server Setup](https://github.com/potatoscript/MyDocuments/blob/main/NLB00.png?raw=true)

- **Servers A and B** work together to handle the traffic.
- **NLB** makes sure no server gets overloaded.
- If one server breaks, **NLB** quickly switches to the backup server.



---

# Network-Load-Balancer
<img src="https://github.com/potatoscript/MyDocuments/blob/main/NLB00.png?raw=true" />
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
