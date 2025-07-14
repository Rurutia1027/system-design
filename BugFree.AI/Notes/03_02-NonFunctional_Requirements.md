# Non-Functional Requirements 
After defining the **functional requirements**, the next step is to establish the **non-functonal requirements(NFRS)**. While functional requirements focus on what the system **should do**, non-functional requirements define **how well** the system performs under various conditions. NFRs describe the system's behavior, ensuring it operates efficiently, reliably, and at scale. 

In system design interviews, discussing non-functional requirements demostrates that you're considering not only the functionality but also the quality and performance aspects of the system. This is crucial for designing scalable and resilient systems.

In this part, we will break down non-functional requirements using the **URL Shortening Service** as an example, covering performance, scalability, reliability, security, and more. 

## What are Non-Functional Requirements?

Non-functional requirements define the qualities of the system, including performance, reliability, security, maintainability, and scalability. These attributes don't directly describe specific features but are critical for ensuring the system can meet user experiences under various conditions. 

Common categories of non-functional requirements include: 

- **Performance**: Response time, latency, and throughput.
- **Scalability**: How the system handles increased load. 
- **Availability**: Uptime and fault tolerance. 
- **Security**: Protection of user data and system integrity.
- **Maintainability**: Ease of updates, debugging, and system monitoring. 


---

# How to Handle Non-Functional Requirements in a System Design Interview 
## Understand the System's Scale and Constraints

## Prioritize Non-Functional Requirements Based on Business Needs 


## Discuss Metrics and Targets 

## Make Design Decisions that Support NFRs


--- 

# Key Non-Functional Requirements and How to Address Them 

## Performance 
- Objective: Ensure the system meets the required response time and throughput under normal and peak loads.
- Key Consideration: Response time (latency), throughput, and the system's ability to handle concurrent requests.

### Design Considerations
- Use **caching** (e.g., Redis, Memcached) to store recently accessed short URLs, reducing database lookups and lowering response times. 
- Implement **horizontal scaling** by adding more application servers to distribute the load. 


## Scalability 
- Objective: Design the system to handle increasing traffic without a drop in performance.
- Key Considerations: The system should scale both vertically (more powerful machines) and horizontally (more machines or instances).

### Design Considerations 
- Implement **sharding** in the database to distribute the load across multiple database servers. 
- Use a **Content Delivery Network(CDN)** to reduce the load on the main servers for static content or assets. 

## Availability and Reliability 
- Objective: Ensure the system is available to users with minimal downtime and can recover from failures quickly.
- Key Considerations: Uptime, fault tolerance, and disaster recovery.

### Design Considerations
- Use redundant servers and deploy across multiple data centers to ensure fault tolerance. 
- Implement database replication (master-slave or master-master) to ensure no single point of failure. 

## Security 
- Objective: Protect the system from unauthorized access, ensure data integrity, and maintain user privacy.
- Key Considerations: Secure data storage, encryption, and access controls. 


### Design Considerations 
- Use SSL/TLS to encrypt all traffic between users and the service. 
- Implement **rate limiting** to prevent abuse, such as spamming the service with thousands of URL shortening requests. 

### Maintainability
- Objective: Ensure that the system is easy to update, monitor, and debug over time. 
- Key Considerations: System monitoring, logging, and ease of software updates. 

### Design Considerations 
- Implement a monitoring system (e.g., Prometheus, Datadog) to track the health of the service and raise alerts when performance drops.
- Use **containrization** (e.g., Docker) and orchestrations tools (e.g., Kubernentes) for easy deployment and scaling of updates. 

## Security 
- Objective: ENsure data is protected and access is controlled.
- Key Considerations: Authentication, encryption, and data privacy. 

