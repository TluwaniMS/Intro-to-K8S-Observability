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

# Distributed Tracing

## What is distributed tracing?

Distributed tracing pertains to techniques for monitoring requests as they traverse across distributed systems. 

It serves as a diagnostic method that unveils the coordination among various services in managing individual user requests. 

Typically, a single trace illustrates the actions involved in an individual transaction or request within the monitored application, tracking the journey from the browser or mobile device to the database and back.

# Anatomy of a trace

Within the context of distributed tracing, a singular trace encompasses a sequence of time intervals labeled as "spans." 

These spans are characterized by both a starting and concluding time, and they may, if needed, incorporate additional information such as logs or tags that aid in characterizing "what occurred." 

Moreover, these spans possess connections with one another, including parent-child associations, which serve to illustrate the precise route a given transaction follows as it traverses the various services or components constituting the application.

- A "Trace" signifies a request that spans from its inception to its completion, comprising either individual or multiple "Spans."

- A "Span" characterizes the work executed by a single service within defined time intervals and comes with accompanying metadata. These "Spans" serve as the fundamental components of a "Trace."

- "Tags" are metadata elements utilized to provide context to a "Span."
