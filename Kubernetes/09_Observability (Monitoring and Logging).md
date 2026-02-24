# ☸️ SECTION 9: Observability (Monitoring & Logging)

### How do you monitor Kubernetes?
> We monitor Kubernetes using metrics and logs.
> Typically, we use Prometheus to collect metrics and Grafana to visualize them.
> We monitor CPU, memory, Pod health, node health, and application metrics.

### What is Prometheus?
> Prometheus is an open-source monitoring tool that collects metrics from Kubernetes components and applications.
> It stores time-series data and allows querying using PromQL.

### What is Grafana?
> Grafana is a visualization tool used to create dashboards for metrics collected by Prometheus.
> It helps visualize cluster performance, application metrics, and alerts.

### What is metrics-server?
> Metrics-server collects basic resource metrics like CPU and memory from nodes and Pods.
> It is mainly used by HPA to scale applications automatically.

### What is kube-state-metrics?
> kube-state-metrics exposes Kubernetes object-level metrics like Deployment status, replica count, and Pod state.
> It helps monitor cluster state.

### What is centralized logging?
> Centralized logging collects logs from all Pods and nodes into a single system.
> This makes troubleshooting easier in distributed environments.

### What is ELK/EFK stack?
> ELK stands for Elasticsearch, Logstash, and Kibana.
> EFK replaces Logstash with Fluentd.
>
> Elasticsearch stores logs, Fluentd collects logs, and Kibana visualizes them.

### How do you monitor cluster components?
> We monitor control plane components like API server, scheduler, and etcd using Prometheus exporters.
> We also monitor node metrics and container runtime metrics.

### How do you implement logging?
> Best practice is to write application logs to stdout and stderr.
> Logging agents like Fluentd collect logs and send them to Elasticsearch or other logging systems.

### How do you debug performance issues?
> To debug performance issues:
>
> * Check resource usage using `kubectl top`
> * Analyze Prometheus metrics
> * Check Pod logs
> * Check node resource pressure
> * Verify HPA behavior
>
> We also check for memory leaks, CPU throttling, or network bottlenecks.

👉 “What are key metrics you monitor?”
> CPU usage, memory usage, Pod restarts, node status, API server latency, request rate, and error rate.