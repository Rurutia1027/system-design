# Design a URL Shortening Service like Bitly 


## High Level Architecture 





---

## Request Flow Sequence 

## API Design 

## Database Design 

--- 
# Fun. / Non-Fun. Requirements 
## Functional Requirements 
- Given a long URL, generate a unique, shortened URL.
- Given a shortened URL, redirect to the original long URL.
- (Optional, if time permits). Allow users to specify a custom short URL alias. 

## Non-Functional Requirements 
- High availability: The service should be available at all times, especially for redirection requests. 
- Low latency: Redirection form short URL to long URL should be fast (e.g., < 10ms).
- Scalability: The system should handle increasing numbers of requests and data growth over time.
- Consistency: Once a short URL is created, it should reliable map to the same long URL.
- Durability: Mappings should not be lost once created. 
- Security: Prevent abuse (e.g., rate limiting, spam detection).

--- 
# Traffic Estimation and Data Calculation 

## Traffic Estimation 
- Assume 100 requests per second for creating short URLs (write requests).
- Assume 10,000 requests per second for redirection (read requests).

## Data Calculation 
Each mapping stores: 
- Short URL key: 8 bytes (e.g., 8-character string)
- Long URL: average 100 bytes 
- Creation timestamp: 8 bytes 
- (Optional) User ID: 16 bytes 
- (Optional) Expiration time: bytes

Total per mapping: ~ 140 bytes (rounded up for metadata and indexing, estimate 160 bytes per entry).
Daily new mappings: 100 req/s * 60 * 60 = 24 = 8,630,000 entries / day 
Daily storage: 8,640,000 * 160 bytes = 1.38GB/day 
Yearly storage: 1.38 * 365 = 504 GB/year 
5-years storage: 504 GB * 5 = 2.5 TB (add buffer, plan for ~ 5TB)
Read traffic: 10,000 req/s  60 * 60 * 24 = 864,000,000 redirections / day 




--- 

# API Design 

--- 
# Database Design 

--- 
# High Level Architecture 

--- 
# Detailed Components Design 

--- 
# Trade-off Discussion 

--- 
# Failure Scenario Discussion 

