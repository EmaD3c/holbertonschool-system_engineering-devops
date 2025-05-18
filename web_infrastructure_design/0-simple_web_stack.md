# Web Infrastructure Explanation

## 1. User Initiates the Request

I'm a user, and I want to access the website by typing `www.foobar.com` in my browser.

## 2. Domain Name System (DNS) Resolution

To do this:
- My browser sends a DNS request to translate `www.foobar.com` (A record) into IP `8.8.8.8`
- The server is located in a data center and can be physical or virtual
- It runs an operating system (typically Linux) hosting all components

## 3. Server Components Overview

1. **Web Server (Nginx)**:
   - Handles HTTP/HTTPS requests
   - Serves static content directly
   - Forwards dynamic requests to application server

2. **Application Server**:
   - Processes business logic (Python/PHP code)
   - Connects to database for data storage/retrieval

3. **Database (MySQL)**:
   - Stores all structured application data
   - Handles SQL queries from application server

4. **Application Files**:
   - Codebase containing website logic
   - Hosted on the same server

## 4. Communication Flow

- **User ↔ Server**: TCP/IP network via HTTP/HTTPS
- **Internal Components**:
  - Web Server ↔ App Server
  - App Server ↔ Database (SQL queries)

## 5. Infrastructure Limitations

1. **Single Point of Failure**:
   - Entire system fails if server fails (no redundancy)

2. **Maintenance Downtime**:
   - Website unavailable during deployments/restarts

3. **Scaling Issues**:
   - Cannot handle traffic beyond single server capacity

4. **Security Risks**:
   - All components on one server increases vulnerability

## Diagram

![](task0_.png)
