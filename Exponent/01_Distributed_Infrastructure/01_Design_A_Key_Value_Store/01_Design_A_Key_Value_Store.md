# Design A Key Value Store 

## 0-5 min: Problem Claification & Scoping 

### Goal: Understand expectations and narrow down the scope.

### Clarifying questions to ask: 
- Is this in-memory (like Redis) or persistent (like DynamoDB) ? 
- Should the system support TTL (Time-To-Live), replication, sharding ? 
- What consistency guarantees are expected? (Strong vs. Eventual)
- Will it be used by internal microservices or public clients ? 
- Expected scale: number of keys? Read/Write ratio? 

### Scoping options: 
- Start with in-memory key-value store (e.g., Redis-like), then evolve to persistent or distributed model. 
- Support basic CRUD: put(key, value), get(key), delete(key)
- Assume values is a blob, and key is a string. 


## 5-10 min: Functional & Non-Functional Requirements 

### Functional: 
- PUT, GET, DELETE, APIs
- Optional: TTL support 
- Optional: Bulk operations or range scan 

### Non-Functional: 
- High availability
- Low latency (e.g., sub-ms reads)
- Horizontal scalability 
- Durability (if persistent)
- Observability (metrics, traces, logs)

__interview tip:Mention SLAs -- e.g., 99.99 uptime, 10ms P95 latency__

## 10-15 min: API Design & Data Modeling 

```
PUT /kv/:key
Body: { "value": "" }

GET /kv/:key

DELETE /kv/:key
```

### Data Model: 
- Key: String 
- Value: Blob or String 
- Optionally: expirationTime (for TTL)
- Optinally: 