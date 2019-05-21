# kubecon-cloudnativecon-europe-2019
Notes taken at Kubecon and Cloud Native Conference Barcelona May 2019

## Day one (Tuesday 21 May 2019)

### Back to Basics: Hands-On Deployment of Stateful Workloads on Kubernetes (Tutorial)
https://kccnceu19.sched.com/event/MPgl/tutorial-back-to-basics-hands-on-deployment-of-stateful-workloads-on-kubernetes-david-zhu-google-jan-safranek-red-hat-limited-availability-first-come-first-served-basis

https://github.com/jsafrane/caas  
Login to GCP console

App deployed at http://35.195.138.121/sample/html

### Day in the life of a Cloud Native Developer (Tutorial)
https://kccnceu19.sched.com/event/MPh0/tutorial-a-day-in-the-life-of-a-cloud-native-developer-randy-abernethy-rx-m-llc-limited-availability-first-come-first-served-basis
Kubernetes, Prometheus, Envoy, Fluentd, gRPC, Containerd, Helm, Harbor and Telepresence

IP 18.197.149.195
Key cnd.pem

https://github.com/RX-M/kubecon-eu-2019

https://zoom.us/j/758119466

**gRPC** stands for gRPC remote procedure call operating over HTTP/2 for transport, protocol buffers for IDL and serialization

**Containerd** - industry-standard container runtime with an emphasis on simplicity, robustness, portability. Has a gRPC API. The OCI container manager under Docker.  Available as a daemon for Linux and Windows.  Manages complete container lifecyle (image transfer, image storage, container execution, container supervision, low level storage, network attachments and more)

**Harbor** is an open source container registry project.  Stores containers, signs containers, scans container content.  Extends open source Docker distribution by adding functionality.

**Kubernetes**, open source container orchestration system. Automates application deployment, scaling, management.

**Helm** is the first application package manager designed by Kubernetes.
A chart is a directory, in the directory you can have many resources.  Allows users to describe application structure through yaml based "helm charts".  Deployed applications can be managed with simple helm commands.  New application can be easily composed of existing loosely coupled microservices.  Users deploying helm charts can tailor them to their needs by settings variables in a values file. Helm chart template is combined with variable values to produce K8s specific configuration file.

**Prometheus** - written in Go used to record real-time metrics in a time series database.
Uses HTTP pull model (scraping metrics from end points using openMetrics format).  Provides flexible timeseries DSL for queries, supports real-time alerting, integrates with K8s, easy to integrate with properly designed microservices, uses Grafana web GUI as a front-end.

**Fluentd** - Data collection tool used for log forwarding, log aggregation.  Used in various roles to create a unified logging layer.  Written in Ruby with core data processing elements in C for performance.
EFK - ElasticSearch - Fluentd - Kibana

**Istio** - Service mesh that provides key cross cutting concerns needed to successfully run a distributed microservice architecture.  Mutual authentication, service to service authorization, traffic management, tracing, monitoring, logging, policy, cluster ingress.  Reduces complexity of managing microservice deployments by providing a uniform way to deploy and manage these services.

**Telepresence** - Lets you run a single service locally while making it act as a component of a remote Kubernetes cluster.  This lets developers working on multi-service applications.  Do fast local development of a single service, even if that service depends on other services in the cluster.  Make a change in the service, build and immediately see the service in action.  Use any tool installed locally to test/debug/edit the service.  Debuggers, IDEs, etc.
Works on Mac and Unix.

### Serverless is interesting but FaaS is not enough (Session)

Industry is moving towards real time data centric streaming apps, automated ops.
Towards fast data, real time, data centric, event driven, "fast data" applications.
Serverless is not function as a service.
Use cases, throughout is key rather than low latency.  Requests can be completed in a short time window.  Like low traffic apps, stateless web apps, parallel processing tasks (resizing images for example), orchestration functions, composing chains of functions, job scheduling.
But it's hard to build general purpose applications.  What is bad…
Retains limitations of 3 tier architecture, no direct accessibility (need storage medium), functions are stateless, ephemeral and short lived, no co-location of state and processing, limited options for managing and coordinating distributed state, limited options for modelling various consistency guarantees.
Support for use cases like.. Training and serving ml models, user sessions, real time distributed stream processing, distributed resilient transactional workflows, shared collaborative workspaces, leader election.
Tech requirements for this to happen: Stateful long loved addressible communication (actors) … and other notes  

Event sourcing  
CRDT - like acid 2.0 (associateive, grouping foesn't matter, communicative, order doesn't matter, etc.)  
Conflict free replicated data types - always converged correctly, is acid 2.0, data types are counters, registers, sets, maps, graphs (that all compose)  

Message in - message out  
Deltas in - deltas out  

Akka - cloud native, reactive, distributed system runtime. Implementation of the actor model, concurrency and distribution.  Good at distributed state management.  See akka.io  

Knative stateful serviing has an akka sidecar.  Powered by akka cluster sidecars.  

Summary  
We have started with Knative, Akka and gRPC.
Serverless 2.0needs a runtime and programming model
https://bit.ly/stateful-serverless-intro  
https://www.github.com/Lightbend/stateful-serverless

