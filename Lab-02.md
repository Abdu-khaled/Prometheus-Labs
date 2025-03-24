## How do I trigger a Prometheus alert?
- we need to create an alerting rule in prometheus alertmanager and then generate conditions in your monitored system that match the rule.

## What is the difference between node exporter and mysql exporter ?
The node exporter and mysql exporter are both part of the prometheus ecosystem, but they serve different purposes:

- Node Exporter:  Collects system-level metrics from a machine (CPU, memory, disk, network, etc.)
- MySQL Exporter:Collects MySQL database-specific metrics.
### And one more thing the mysql exporter run in foreground by default but node exporter run in background 

--- 


## What is the maximum retention period to save data in Prometheus and how to increase it ?

- By default prometheus stores time-series data for 15 days in its local storage.

- There is no max hard limit for retention period in prometheus but we can configure it for store data for month or year it depending on available disk space bro. 

- so how we can configure it 
    - You can extend the data retention period using the --storage.tsdb.retention.time flag when starting prometheus we can update prometheus service file and add this command line with any retention time we need example 

    ```
    --storage.tsdb.retention.time=100d
    ```

--- 
## What are the different PromQL data types available in Prometheus Expression language?

PromQL (Prometheus Query Language) has four main data types, which are used for querying and manipulating time-series data.

1. Scalar (Instant Value)
    - A single numeric value (floating point).
    - Represents a constant at a specific time.

2. Instant Vector
    - A set of time-series data points at a single timestamp.
    - It includes metric names, labels, and values.

3. Range Vector
    - A set of time-series data over a time range.
    - sed in functions that need historical data, such as rate calculations.

4. String (Experimental)
    - Strings are not widely used in PromQL, as Prometheus mainly deals with numerical data.
    - Some API responses return metadata as strings. 

---

## How To calculate the average request duration over the last 5 minutes from a histogram ?

```
rate(http_request_duration_seconds_sum[5m]) / rate(http_request_duration_seconds_count[5m])

```

--- 

## What is Thanos Prometheus?

Thanos is an open-source project that extends Prometheus for long-term storage, high availability, and global querying across multiple Prometheus instances.

If we need long-term storage (months/years of metrics) or we  have multiple Prometheus instances and need a single view or we want high availability and failover for monitoring.

--- 

## What is promtool and how i can use it ?
promtool is a command-line tool provided with Prometheus that helps validate, debug, and test Prometheus configurations, rules, and TSDB data.

--- 

## What types of Monitoring can be done via Grafana?

Grafana supports a wide range of monitoring use cases including: Infrastructure (Servers, Containers, Kubernetes)
- Application & Database Performance
- Network & Security Monitoring
- Business Analytics & IoT Metrics
- Synthetic Monitoring for Uptime & SLAs


--- 
## Can we see different Servers CPU comparison in Grafana

Grafana allows you to compare CPU usage across multiple servers by querying Prometheus.

