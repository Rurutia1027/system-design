# Redis in System Design: Stories, Features, and Notes 
## Atomicity and Concurrency Control (Auditor Use Case)
**Scenario**:
You're building a support tools that keeps **audit trails** of user actions or service changes. 

**Where Redis Helps**:
- Use atomic **LPUSH** or **XADD(Streams)** to log actions without risk of concurrent loss. 
- You can push aduit logs into Redis, and process them asynchronously (e.g., to a database later).

## Redis Pipeline -- What is it? 
**Definition**:
Redis Pipeline allows you to send multiple commands in one go over the network, reducing latency caused by round trips. 

```
[send 100 commands at once] -> [Redis executes them all] -> [return 100 responses]
```
**When to Use**
- High-throughput scenarios: bulk logging, syncing, caching precomputed data.
- Auditor systems writing massive numbers of events quickly.
- Startup scripts that preload data into Redis efficiently.

# Data Integrity + Consistency Under Load 
Redis is in-memory and **eventually persistent (via RDB/AOF), so in critical systems:
- Use Append-Only File (AOF) to recover lost data in crash scenarios. 
- Combine Redis wiht a **durable backend** for long-term retention. 

**System Design Insight**:
- We treate Redis as a high-speed cache and buffer. Logs and events entered Redis first for real-time needs, and we periodically flushed batches to our database to ensure durability.

# Queueing + Rate Limiting + Throttling Auditors 
Redis helps with 
- Task queue (with LIST, BRPOPLPUSH)
- Leaky bucket / token bucket for request limiting.
- Fairness across consumers using Redis Streams 

"We had multiple auditors ingesting events in parallel, but used Redis Streams to ensure message order and prevent duplicate processing".


# Concurrency Safe Counters 
Example Use Case:
Auditor needs to count: 
- Number of times a user triggered a particular action 
- Number of retries per serivce 
- Daily error quotas 

Redis gives:
- Atomic INCR, HINCRBY 
- Expiring counters using EXPIRE 

# Patterns to Talk About in Interviews 
## Event Buffer 
- LIST, LPUSH, BRPOP
- Smooth bursty traffic from support tools or log collectors 

## Batch Writes 
- Pipeline 
- Reduce round-trip latency in bulk operations 

## Atomic Locks 
- SETNX or Redis Lock 
- Prevent double processing in distributed systems 

## Token Bucket 
- DECR, Lua
- Control API usage under concurrency pressure 
  
## Idempotency 
- SETNX with TTL 
- Ensure retry-safe write without duplicates
  
## Ephemeral Counters 
- INCR + EXPIRE 
- Count transient things (like errors/minute)
