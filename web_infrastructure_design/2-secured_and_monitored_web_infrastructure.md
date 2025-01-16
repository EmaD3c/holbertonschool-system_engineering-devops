# Secured and Monitored Web Infrastructure

## 1. User Accesses the Website
As a user, I type **www.foobar.com** into my browser. My browser sends a DNS request to resolve the domain name into an IP address. The DNS server responds with the IP address of the load balancer.

---

## 2. HTTPS Request to the Load Balancer
My browser sends an **HTTPS request** to the load balancer using the provided IP address. The load balancer, secured with an **SSL certificate**, terminates the SSL connection to decrypt the request and ensures encrypted traffic between the user and the server.

---

## 3. Load Balancer Distributes Traffic
The load balancer determines which application server to send the request to, using a **round-robin algorithm** for even distribution. This ensures that no single server is overwhelmed with requests.

---

## 4. Firewall Protects Each Component
Each server in the infrastructure is protected by a **firewall**:
- The firewall blocks unauthorized traffic and ensures only valid requests reach the servers.
- This includes rules for HTTP/HTTPS traffic and restricted database access.

---

## 5. Application Server Processes the Request
The application server, which hosts the website’s codebase, processes the dynamic content of the request. For example:
- If the request is for user data, the application server queries the **Primary database**.

---

## 6. Database Handles the Request
The **Primary MySQL database** handles write operations (e.g., updates or inserts), while the **Replica database** serves read operations to improve performance and reliability.

---

## 7. Monitoring Collects Metrics
Each server is equipped with a **monitoring client** (e.g., Sumo Logic or Prometheus) that:
- Tracks metrics like server load, query per second (QPS), and traffic patterns.
- Sends collected data to a centralized monitoring service for real-time analysis and alerts.

---

## 8. Response Sent Back to the User
Once the application server completes processing the request:
1. It sends the data back to the load balancer.
2. The load balancer forwards the response to the user’s browser over HTTPS.
3. The browser renders the webpage, and the user can now interact with the site.

---

## Issues with the Infrastructure
1. **SSL Termination at the Load Balancer**: 
   - Traffic between the load balancer and backend servers is not encrypted.
   - To address this, enable HTTPS end-to-end encryption.

2. **Single Primary Database**:
   - A single writable database creates a bottleneck.
   - Implement failover mechanisms or sharding for better scalability.

3. **Identical Servers**:
   - Having the same components on all servers reduces specialization.
   - Use dedicated servers for specific roles (e.g., separate application and database servers).


![](task3_.png)
