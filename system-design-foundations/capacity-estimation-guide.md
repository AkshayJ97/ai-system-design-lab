# Capacity Estimation Guide: Swiggy-like System

## Overview
This guide provides frameworks and formulas for estimating system capacity requirements including RPS (Requests Per Second), storage, and bandwidth for a large-scale food delivery platform.

---

## 1. Core Metrics

### DAU (Daily Active Users)
- **Definition**: Number of unique users who interact with the system in a 24-hour period
- **Example**: 2M DAU

### MAU (Monthly Active Users)
- **Definition**: Number of unique users who interact with the system in a 30-day period
- **Typical Ratio**: MAU = DAU × 2.5 to DAU × 4
- **Example Calculation**: 2M DAU × 3 = **6M MAU**

### Peak Time Distribution
- Peak hours typically: 8-10 AM (breakfast), 12-1 PM (lunch), 7-9 PM (dinner)
- Peak hour traffic: ~3-4x average traffic
- Peak second traffic: ~2-3x peak hour average

---

## 2. RPS (Requests Per Second) Estimation

### Formula
```
RPS_avg = (DAU × avg_requests_per_day) / 86400
RPS_peak = RPS_avg × peak_multiplier (2-3x)
```

Where:
- **DAU**: Daily Active Users
- **avg_requests_per_day**: Average API calls per user per day
- **86400**: Seconds in a day
- **peak_multiplier**: 2 to 3x factor during peak hours

### Request Types & Frequencies
For a food delivery platform:
- **Browse/Search**: ~15 requests/day per user
- **Place Order**: ~1 request/day per user
- **Order Status**: ~5 requests/day per user
- **Chat/Notifications**: ~10 requests/day per user
- **Payments/Checkout**: ~2 requests/day per user
- **Backend Cron/Analytics**: ~5 requests/day per user

**Total avg_requests_per_day = 38 requests/user/day**

---

## 3. Worked Example: 2M DAU System

### 3.1 Average RPS Calculation
```
RPS_avg = (DAU × avg_requests_per_day) / 86400
RPS_avg = (2,000,000 × 38) / 86400
RPS_avg = 76,000,000 / 86400
RPS_avg = 878.7 RPS (average)
```

### 3.2 Peak RPS Calculation (2.5x multiplier)
```
RPS_peak = RPS_avg × peak_multiplier
RPS_peak = 878.7 × 2.5
RPS_peak = 2,196.75 ≈ 2,200 RPS (peak)
```

### 3.3 Conservative Estimate (3x multiplier)
```
RPS_peak = RPS_avg × 3
RPS_peak = 878.7 × 3
RPS_peak = 2,636.1 ≈ 2,650 RPS (conservative peak)
```

**Recommendation**: Provision for **2,200-2,650 RPS** at peak load.

---

## 4. Storage Estimation

### Formula
```
Total_Storage = (Users × avg_data_per_user) + app_data + logs + backups
```

Where:
- **Users**: Total registered users (typically 2-3x DAU)
- **avg_data_per_user**: Profile data, orders, preferences
- **app_data**: Code, configs, static files
- **logs**: Transaction and audit logs
- **backups**: Redundancy copies

### Data Breakdown per User
- **User Profile**: ~2 KB (name, phone, email, addresses)
- **User Orders (1-year history)**: ~100 KB (300 orders × 300 bytes average)
- **User Preferences/Favorites**: ~50 KB (bookmarked restaurants, dietary preferences)
- **Session/Cache Data**: ~10 KB

**Total per user: ~162 KB**

### 3.4 Storage Calculation (2M DAU, 6M Total Users)

```
User_data_storage = 6,000,000 users × 162 KB
User_data_storage = 6,000,000 × 0.162 MB
User_data_storage = 972,000 MB = ~972 GB ≈ 1 TB

App_data (restaurants, items, images, configs) = ~50 GB
Transaction_logs (1 year): 
  - Avg 200 bytes per transaction
  - 2M DAU × 1 order/day × 365 days = 730M transactions/year
  - 730M × 200 bytes = 146 GB

Backups (3x redundancy):
  - (1,000 GB + 50 GB + 146 GB) × 3 = ~3,438 GB ≈ 3.5 TB

Total Storage Required: ~5.5 TB (primary + backups)
```

**Recommendation**: Use distributed database with sharding. Allocate **5-6 TB** including backups and redundancy.

---

## 5. Bandwidth Estimation

### Formula
```
Bandwidth_bps = (RPS_peak × avg_payload_size_bytes × 8) / 1_000_000_000
Bandwidth_Gbps = Bandwidth_bps / 1,000,000,000
```

Where:
- **RPS_peak**: Peak requests per second
- **avg_payload_size_bytes**: Average request + response size
- **8**: bits per byte
- **1_000_000_000**: conversion to Gbps

### Payload Breakdown
- **Average Request**: ~2 KB (search, order placement, status check)
- **Average Response**: ~5 KB (order details, restaurant data, maps)
- **Total Request-Response**: ~7 KB per request

### 3.5 Bandwidth Calculation (Peak 2,200 RPS)

```
Bandwidth_bits_per_second = 2,200 RPS × 7,000 bytes × 8 bits/byte
Bandwidth_bits_per_second = 2,200 × 7,000 × 8
Bandwidth_bits_per_second = 123,200,000 bits/second
Bandwidth_bits_per_second = ~123 Mbps

Bandwidth_Gbps = 123 Mbps / 1,000 = 0.123 Gbps ≈ 125 Mbps
```

### Including Overhead (2x for redundancy, retries, headers)
```
Bandwidth_required = 125 Mbps × 2 = 250 Mbps ≈ 0.25 Gbps
```

**Recommendation**: Provision for **0.25-0.5 Gbps** at peak (accounting for CDN, caching, and edge distribution).

---

## 6. Complete Capacity Summary: 2M DAU System

| Metric | Value | Notes |
|--------|-------|-------|
| **DAU** | 2,000,000 | Baseline |
| **MAU** | 6,000,000 | 3x DAU |
| **Avg RPS** | ~879 | Baseline throughput |
| **Peak RPS** | 2,200 - 2,650 | 2.5x-3x multiplier |
| **Primary Storage** | ~1 TB | User & order data |
| **Total Storage (with backups)** | ~5-6 TB | 3x redundancy |
| **Peak Bandwidth** | 0.25-0.5 Gbps | With overhead |

---

## 7. Server Capacity Breakdown

### Assuming 20 RPS per server (conservative)
```
Servers_needed = RPS_peak / RPS_per_server
Servers_needed = 2,200 / 20
Servers_needed = 110 servers
```

With 3x redundancy (active-active-active):
```
Total_servers = 110 × 3 = 330 servers (minimum)
```

### Database Shards
Assuming 10M entries per shard with 6M users:
```
Shards_needed = 6,000,000 / 10,000,000 = 1 shard (minimum)
Recommendation: 3-5 shards for horizontal scaling + 1 replica per shard
Total DB instances: 12-15
```

---

## 8. Caching Strategy Impact

### Cache Hit Rate Optimization
- **L1 Cache (Redis, In-memory)**: 80-90% hit rate
  - Reduced to effective RPS: 2,200 × 0.15 = **330 RPS** to database
  
- **L2 Cache (CDN for static content)**: 95%+ hit rate
  - Reduces bandwidth from 0.25 Gbps to **0.05-0.1 Gbps**

---

## 9. Capacity Planning Timeline

| Phase | DAU | RPS Peak | Storage | Servers |
|-------|-----|----------|---------|---------|
| **Year 1** | 2M | 2,200 | 5 TB | 110-115 |
| **Year 2** | 5M | 5,500 | 12 TB | 275-300 |
| **Year 3** | 10M | 11,000 | 24 TB | 550-600 |

---

## 10. Key Considerations

### Database Selection
- **Write-heavy**: Use clock-skewed writes with eventual consistency (Cassandra, DynamoDB)
- **Strong consistency**: PostgreSQL with replication (for financial transactions)
- **Time-series**: InfluxDB for metrics and analytics

### Load Balancing
- Use consistent hashing for cache distribution
- Implement circuit breakers for downstream services
- Monitor server health every 5-10 seconds

### Monitoring Thresholds
- **RPS threshold for scaling**: 80% of capacity
- **Memory threshold**: 85%
- **Disk I/O threshold**: 75%

---

## 11. Safety Margin Formula

```
Capacity_provisioned = (Expected_load × 1.5) + (Peak_spike × 0.5)
```

For our system:
```
Capacity_provisioned = (2,200 × 1.5) + (Unexpected_spike × 0.5)
Capacity_provisioned ≥ 3,300 RPS capacity
```

This ensures 50% headroom for unexpected traffic spikes.

---

## References
- Industry benchmarks: 15-40 RPS per server (depends on compute)
- Twitter: ~5,500 tweets/second average, ~143K at peak (2013)
- Swiggy/Zomato: Estimated 10,000+ RPS at peak (2024)
