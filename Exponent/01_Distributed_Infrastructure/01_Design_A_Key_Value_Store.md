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
- Optinally: Metadata (timestamps, access counters)

__Optional: Include versioning or CAS (Compare-And-Swap) for atomicity__


## 15-20 min: Capacity Estimation 
### Assume:
- 500M keys 
- Avg key size = 32 bytes 
- Avg value size = 512 bytes 

### Memory：
- 500M * (32 + 512) = ~ 260 GB total raw data 
- Add 20% overhead -> 312 GB

### QPS:
- Reads: 100K QPS 
- Writes: 10K QPS 

### Disk (if our design includes persistent):
- Daily writes: 10K * 86400 = ~864M writes/day 
- With 512B -> 422 GB/day writeen 

__Interview tips here: Show comfort estimating sizes, throughput, and data growth. Talk about replication factor's impact__

## 20-30 min: High-Level Design + Component Breakdown 
### Components
- API Gateway (handles REST)
- KV Router (routes request based on consistent hashing)
- Shared Nodes (handle storage & retrival)
- Replication Manager (ensures HA)
- Write-Ahead Log / Persistence Engine (for durability)
- Cache Layer (optional LRU cache)

### Data Flow(* important *)
- PUT: API -> Router -> Shard -> Memory Store -> WAL (if persistent)
- GET: API -> Router -> In-Memory -> Fallback to Disk (optional)

__Bonus: Mention gossip protocol or heartbeat mechanism for cluster health__

## 30 - 35 min: Trade-offs & Reliability 

