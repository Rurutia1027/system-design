# Database Design 

Database design is a critical part of system design, as it determines how data is stored, retrieved, and managed. A well-designed database ensures that the system is scalable, performs efficiently, and can handle large volumes of data. Poor database design can lead to bottlenecks, performance issues, and complexity in maintaining the system over time. 

In system design interviews, database design demostrates your ability to choose the right data storage solutions, model the data effectively, and optimize for scalability and performance. In this section, we'll dive into database design concepts, using the URL Shortening Service as our example. 

--- 

# What is Database Design 
Database design is the process of deciding how to structure and organize the data that your system gonna store. This includes: 
- Choosing the database type (SQL vs. NoSQL)
- Defining the data schema (tables, columns, relationships)
- Optimizing for performance (indexing, partitioning, caching)
- Ensuring scalability and consistency
The goal is to design a database that supports your system's functional requirements (e.g., storing and retrieving data efficiency) and non-functional requirements (e.g., handling high traffic and ensuring data itnegrity).


--- 

# Best Practices for Database Design 
- Denomalize for Performance: In NoSQL databases, it's common to denormalize data (i.e., store redundant copies of data) to optimize read performance. For example, you might store the `click_count` directly in the `URLs` record rather than calculating it on the fly.
- Optimize Queries: Ensure that your queries are efficient. For example, querying by `short_url` should be fast because it uses the primary key in a NoSQL database. 
- Use Appropriate indexes: Index the fields you commonly query. For example, if you often query URls by creation date, index the `created_at` field for faster lookups. 
- Plan for Data Growth: As your system grows, ensure that your database design can handle large amounts of data. Techniques like sharding and partitioning will help scale the system horizontally.
- Backup and Disaster Recovery: Implement backup strategies to ensure data recovery in case of failure, Regularly backup critical data and have a plan for restoring it. 

---

# Common Mistakes to Avoid 
- Over-normalizing in NoSQL: Don't try to design a NoSQL database liek a relational database. Avoid creating too many relatonships and joins; instead, focus on optimizing for reads with denormalized data. 
- Not planning for scale: If you expected high traffic,plan for scalability early on. Ensure your database can handle large volumes of data and traffic spikes. 
- Ignoring indexing: Failing to index key fields can result in slow queries and poor performance, especially as the dataset grows. 
- Lack of backups: Always have a backup and recovery plan. Data loss due to a lack of backups can be catastrophic. 
