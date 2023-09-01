# Intro-to-K8S-Observability

# What is observability ?

The conventional understanding of observability in the context of distributed systems has traditionally revolved around three core elements:

gathering time-based metrics, consolidating logs, and conducting request traces as they traverse your system.

# The three pillars of observability:

* Metrics
* Logs
* Tracing


# Monitoring:

# The two types of monitoring: 

i. Blackbox Monitoring:
* Measurement from outside
* Hardware issues
* CPU load average
* Hypervisor-level metrics

ii. Whitebox monitoring:
* Inside Knowledge of a system
* Mysql Query time 
* HTTP Requests
* Service Traffic Patterns


`NB!`

`Observability provides both blackbox and white box monitoring, to give more context.`

# Kubernetes Logging

Application logs provide insights into the internal workings of your application, serving as valuable tools for troubleshooting issues and overseeing cluster operations.

The most straightforward and widely embraced logging approach for containerized applications involves directing log output to standard output and standard error streams.

Within a cluster environment, it's advisable for logs to be managed independently of nodes, pods, or containers, with a dedicated storage system and lifecycle. This approach is commonly referred to as "cluster-level logging."

To implement cluster-level logging, you'll need a distinct backend system for storing, analyzing, and querying logs.
