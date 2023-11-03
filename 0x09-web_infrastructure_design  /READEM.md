README for Web Infrastructure Design
0-simple_web_stack
Web Infrastructure Design

Server (8.8.8.8): A physical or virtual machine where all components of the web infrastructure reside.

Domain Name: A human-readable address used to access the website, in this case, www.foobar.com. The domain name is mapped to the server's IP address (8.8.8.8) using DNS records.

DNS Record: A DNS (Domain Name System) record is a mapping between a domain name and an IP address. In this case, the www record in www.foobar.com points to the server's IP address 8.8.8.8.

Web Server (Nginx): Nginx is the web server software responsible for handling incoming HTTP requests from users' web browsers. It serves static content and can also act as a reverse proxy to forward dynamic requests to the application server.

Application Server: The application server hosts the website's application code. It processes dynamic requests, executes the application logic, and generates dynamic content. For example, it can run a Python, Ruby, or PHP application.

Application Files (Code Base): The application files contain the source code, scripts, and necessary assets that constitute the website. These files are executed by the application server to generate dynamic web pages.

Database (MySQL): MySQL is a relational database management system. It stores and manages the website's data, such as user information, content, and other relevant data. The application server communicates with the database to fetch or store data as needed.
1-distributed_web_infrastructure
Load Balancer (HAproxy):

Why: Load balancers distribute incoming network traffic across multiple servers to ensure no single server is overwhelmed, improving performance and redundancy.

Distribution Algorithm: Round Robin. It forwards requests to the servers in a circular order.

Active-Active or Active-Passive: Active-Passive. In an Active-Passive setup, one server handles traffic while the other is on standby, ensuring failover capability if one server fails.
Web Servers (Nginx) - Server 1 and Server 2:

Why: Web servers handle HTTP requests from clients, serving static content and forwarding dynamic content requests to the application server.

Nginx: Nginx is lightweight, efficient, and can handle concurrent connections efficiently.
Application Server:

Why: The application server executes dynamic content and processes application logic before sending responses back to the web server for client delivery.

Application Files: Hosted on both servers. These files contain the codebase and assets required to run the website.
Database (MySQL - Primary-Replica Cluster):

Why: Databases store and manage website data. A Primary-Replica cluster ensures data redundancy and high availability.

Primary-Replica Cluster: The primary node handles write operations, replicating data to the replica node. Read operations can be distributed between both nodes, improving performance.
2-secured_and_monitored_web_infrastructure
Web Infrastructure Design:

Servers:

Load Balancer (LB): Terminates SSL connections. Distributes traffic among the three servers. Acts as the entry point for all incoming traffic.

Web Servers (Server 1, Server 2, Server 3): Host the website content and applications. Serve web pages to clients. Communicate with the database server.

Database Server (MySQL): Stores website data, user information, etc. Handles database read and write operations.

Additional Elements:

Firewalls: Placed around each server to filter incoming and outgoing network traffic. Protect servers from unauthorized access and potential threats.

SSL Certificate: Installed on the load balancer. Encrypts data transmitted between clients and the web servers. Ensures secure communication and prevents eavesdropping.

Monitoring Clients (Sumo Logic Data Collectors): Installed on each server. Collects performance metrics, error logs, and other data. Sends data to Sumo Logic or other monitoring services for analysis.
3-scale_up
Overview

This document outlines the design and implementation of a scalable, redundant, and secure web application infrastructure. The infrastructure includes a web server, an application server, and a database server, all split into separate components to enhance security and performance. Additionally, a load balancer (HAProxy) is configured as a cluster to distribute traffic effectively, ensuring high availability and load balancing.
Infrastructure Components

    Web Server (Server 1):
        Purpose: The web server handles incoming HTTP requests, serving static content, and acting as a reverse proxy for dynamic content.
        Specifics: Nginx is chosen as the web server due to its efficiency, low resource usage, and excellent support for serving static content and proxying requests to the application server.

    Application Server (Server 2):
        Purpose: The application server processes dynamic content, executes server-side logic, and communicates with the database server.
        Specifics: Node.js is chosen for its non-blocking, event-driven architecture, making it suitable for handling concurrent connections and asynchronous I/O operations.

    Database Server (Server 3):
        Purpose: The database server stores and retrieves application data, ensuring data integrity and consistency.
        Specifics: PostgreSQL, a robust, open-source relational database system, is chosen for its ACID compliance, extensibility, and support for complex queries.

    Load Balancer (HAProxy Cluster):
        Purpose: The HAProxy load balancer distributes incoming traffic across multiple web server nodes, ensuring high availability and load balancing.
        Specifics: HAProxy is configured as a cluster, with failover mechanisms and health checks to reroute traffic in case of server failures.
