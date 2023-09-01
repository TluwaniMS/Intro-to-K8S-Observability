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

`NB!`

`Kubernetes does not provide a native storage solution for log data.`

# Cluster-level logging architectures

### Available options for cluster level logging:

1. Employing a node-level logging agent on each node is the initial step in establishing cluster-level logging. This dedicated logging agent tool either exposes or sends logs to a backend. Typically, this agent is encapsulated within a container, granting it access to a directory housing log files from all application containers on that particular node.

2. Within an application pod, there exists a dedicated sidecar container designed specifically for handling logging tasks. This sidecar container actively streams application logs to its own standard output. It is equipped with a logging agent configured to retrieve logs from an application container. These sidecar containers are capable of reading logs from various sources such as files, sockets, or journald, and each of them forwards logs to its respective standard output or standard error stream.

3. Alternatively, logs can be directly pushed to a backend from within an application. However, it's important to note that cluster-level logging, which involves exposing or pushing logs from every application, falls outside the purview of Kubernetes.
