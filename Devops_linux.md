### DevOps engineer working with Linux need to know these:

1. **SSH (Secure Shell)**:
    -  Port: 22
    -  Purpose: Used for secure remote login and command execution on Linux servers.
    -  Use Case: Admin access to servers, deploying code, configuration management.
    -  Example Tool: ssh, scp, rsync.

2.  **HTTP (Hypertext Transfer Protocol)**
    -  Port: 80
    -  Purpose: Used by web servers to serve unencrypted HTTP traffic.
    -  Use Case: Web applications, load balancing, reverse proxy setup.
    -  Example Tool: nginx, apache2.

3.  **HTTPS (Hypertext Transfer Protocol Secure)**
    -  Port: 443
    -  Purpose: Encrypted web traffic, used for secure communications.
    -  Use Case: Hosting secure web applications, SSL/TLS termination.
    -  Example Tool: nginx, apache2, letsencrypt.

4.  **FTP (File Transfer Protocol)**
    -  Port: 21
    -  Purpose: Used for transferring files between servers.
    -  Use Case: File transfer between systems (though often replaced by SFTP for security reasons).
    -  Example Tool: vsftpd, proftpd.

5.  **SFTP (SSH File Transfer Protocol)**
    -  Port: 22 (Same as SSH)
    -  Purpose: Secure file transfer using SSH.
    -  Use Case: Secure file uploads/downloads to remote systems.

6.  **DNS (Domain Name System)**
    -  Port: 53
    -  Purpose: Resolves domain names to IP addresses.
    -  Use Case: Networking, troubleshooting, service discovery.
    -  Example Tool: bind9, dnsmasq, systemd-resolved.

7.  **MySQL / MariaDB**
    -  Port: 3306
    -  Purpose: Default port for MySQL and MariaDB databases.
    -  Use Case: Database management, application backends.
    -  Example Tool: mysql, mariadb.

8.  **PostgreSQL**
    -  Port: 5432
    -  Purpose: Default port for PostgreSQL databases.
    -  Use Case: Application backends, data storage.
    -  Example Tool: postgresql.

9.  **Redis**
    -  Port: 6379
    -  Purpose: Default port for Redis in-memory data store.
    -  Use Case: Caching, message brokering, session management.
    -  Example Tool: redis-server.

10. **MongoDB**
    -  port: 27017
    -  Purpose: Default port for MongoDB NoSQL database.
    -  Use Case: NoSQL data storage.
    -  Example Tool: mongod.

12. **Jenkins**
    -  Port: 8080
    -  Purpose: Default port for Jenkins CI/CD server.
    -  Use Case: Continuous integration and deployment.
    -  Example Tool: jenkins.

13. **Docker**
    -  Port: 2375 (unencrypted), 2376 (encrypted)
    -  Purpose: Default port for Docker daemon's REST API.
    -  Use Case: Docker container orchestration, remote management.
    -  Example Tool: docker, docker-compose.

14. **Kubernetes API Server**
    -  Port: 6443
    -  Purpose: Default port for the Kubernetes API server.
    -  Use Case: Kubernetes cluster management, service discovery.
    -  Example Tool: kubectl, helm.

15. **ElasticSearch**
    -  Port: 9200 (HTTP), 9300 (Internal communication)
    -  Purpose: Default port for Elasticsearch REST API and cluster communication.
    -  Use Case: Full-text search, log aggregation.
    -  Example Tool: elasticsearch.

16. **RabbitMQ**
    -  Port: 5672
    -  Purpose: Default AMQP (Advanced Message Queuing Protocol) port.
    -  Use Case: Messaging queues, event-driven architectures.
    -  Example Tool: rabbitmq.

17. **Grafana**
    -  Port: 3000
    -  Purpose: Default port for Grafana, a popular open-source dashboarding tool.
    -  Use Case: Cloud monitoring, visualizing metrics from various sources like Prometheus or Elasticsearch.
    -  Example Tool: Grafana.

18. **Prometheus**
    -  Port: 9090
    -  Purpose: Default port for Prometheus server to scrape metrics.
    -  Use Case: Monitoring and alerting based on time-series data.
    -  Example Tool: Prometheus.
