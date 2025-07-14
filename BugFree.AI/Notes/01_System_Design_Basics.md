# What's System Design ? 
## Introducion to System Design 
System design refers to the process of definining the architecture, components, modules, interfaces, and data of a system to satisfy specified requirements. In essence, it is the blueprint that helps engineers create efficient, scalable, and maintainable software systems. 

Unlike algorithm or coding interviews, system design questions focus on your ability to create high-level solutions to complex problems. You'll be asked to outline how to build robust systems that scale well and handle edge cases, all while balancing trade-offs like **performance**, **cost**, and **complexity**.

## Why Is System Design Important ?
System design is critical for several resources:

- **Scalability**: As companies grow, their systems must be able to handle an increasing load of data and users. Designing for scalability ensures that the system can grow without significant redesign. 
- **Reliability**: Users expect systems to work seamlessly. Poorly designed systems often face issues such as downtime or data loss, which can damage both a company's reputation and revenue. 
- **Performance**: Fast and efficient systems are vital for a good user experience. System design ensures that your system performs well, even under heavy usage. 
- **Maintainability**: A well-designed system should be easy to update and maintain as technologies evolve and requirements change. 
- **Security**: Protecting data and preventing breaches is a key component of system design, especially in today's world of increasing ly sophisticated cyber threats. 

## System Design vs. Coding Interviews 
While coding interviews focus on implementing algorithms and solving programming languages, system design interviews asssess your ability to think at a higher level. In coding interviews, you're often concerned with time and space complexity for small problems, but in system design, you are required to :
- Think about large-scale systems with multiple interacting components. 
- Consider real-world factors such as latency, throughput, and data storage. 
- Make trade-offs between different design choices (e.g., speed vs. cost, simplicity vs. flexibility).
- Design systems that can scale to millions of users. 

**System design is about creating solutions that are not only technically feasible but also practical and future proof.**


## Key Concepts is System Design 
## Scalability 
- Horizontal vs. vertical scaling: Learn how systems can scale by adding more servers (horizontal) or upgrading existing hardware (vertical).
- Load balancing: Distributing incoming traffic to multiple servers to ensure a smooth user experience. 

## Availability and Reliability 
- High availability (HA): Designing systems that minimize downtime, often by incorporating redundancy (e.g., multiple data centers).
- Fault tolerance: How a system continues to operate even in the case of failures. 

## Consistency and Partition 
- CAP theorem: Understand the trade-offs between Consistency, Availability, and Partition tolerance in distributed systems. 
- Data partition (sharding): Splitting data into smaller, manageable pieces to improve performance and scalability.

## Latency and Throughput 
- Latency: The time it takes for a request to be processed (on the server side).
- Throughput: The number of requests a system can handle per unit of time. 

## Caching 
- Reducing the load on your system by storing frequently accessed data in a cache, which improves speed and performance. 

## Databases and Storage 
- Relational vs. NoSQL databases: When to use each type and how they fit into different design scenarios.
- Data replication and backups: Ensuring data availability and disaster recovery.


## Security 
- Autentication and authorization: Controlling access to your system and its data. 
- Encryption: Protecting data in transit and at rest. 
- Rate limiting and DDoS protection: Preventing abuse and attacks. 