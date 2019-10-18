---
title: Kubernetes
description: 
published: true
date: 2019-10-18T11:46:19.612Z
tags: 
---

# What is Kubernetes?

[Kubernetes](https://kubernetes.com/), aka _k8s_ or _kube_, is an open-source system for deploying, scaling, and managing containerised applications in an automated fashion across a group or cluster of server machines. It works with a range of container tools, including [Docker](https://www.docker.com/). Originally developed by Google, it was open-sourced in 2014 and is now run by the [Cloud Native Computing Foundation](https://www.cncf.io/), a community project under the aegis of the non-profit [Linux Foundation](https://www.linuxfoundation.org/).

Containers are similar to virtual machines, with isolated environments and a separation of concerns, but much more lightweight and flexible. Containers provide an approach where you package different services into separate containers and deploy them across a cluster of machines (physical or virtual). Kuberenetes is here to help you automate the deployment, management, scaling, networking, and availability of these containers.

Things you can do with the help of Kubernetes:

- Deploy multi-container applications
- Automate load balancing
- Upgrade applications without downtime
- Monitor containers and applications
- Provide persistent storage for containers

Kubernetes is not a platform-as-a-service (because it operates on containers not hardware) and does not demand particular applications or languages. It doesn't deploy or build your software, and it doesn't provide machine configuration or maintenance.

## Words to memorise so you sound like you know what you're talking about

- _Cluster_: a group of machines with a master/slave setup
- _Node_: a physical or virtual machine within a cluster
- _Pod_: a group of one or more containers deployed to a single node and sharing an IP address
- _Service_: a load balancer for accessing pods, so that the right pod gets the right request no matter if it's moved or replaced
- _Volume_: a location where containers can access and store information
- _Replication controller_: a method for managing identical copies of of pod within a cluster
- _Deployment_: a YAML blueprint describing how pods should be created

To help organise and isolate clusters, nodes, pods, etc, Kuberneters offers _labels_ (key/value pairs used to identify things) and _namespaces_ (a grouping mechanism that provides a degree of isolation from other parts of the cluster).

## Architecture

The [architecture of Kubernetes is well-explained](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/architecture/architecture.md) in a document in the Kubernetes repo on GitHub. [New Relic also do a good job in a blog post](https://blog.newrelic.com/engineering/what-is-kubernetes/) (see section "So, how does Kubernetes work?").

The central component of Kubernetes is the _cluster_: a collection of physical or virtual machines, each of which serve as either the master or a node. The master is the access point (["control plane"](https://en.wikipedia.org/wiki/Control_plane)) used to manage the scheduling and deployment of containers within the cluster. In a complex cluster there may be more than one master.

_Masters_ communicate with the rest of the cluster through the [API server](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/), and store the state and configuration data for the entire cluster using a persistent, distributed key-value store called [etcd](https://github.com/etcd-io/etcd). The master tracks node capacity and resources using the [scheduler](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-scheduler/), which assigns work to work to nodes based on their availability. Deployments, replicas, and health checks are handled by the [controller manager](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-controller-manager/).

If it's not a master, than a physical or virtual machine is a _node_. All nodes have a container runtime, typically Docker. Your application code runs inside the containers. Each node runs a [kubelet](https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/): an agent process responsible starting, stopping, and maintaining the node's application containers. To do this, it takes instructions from the master.

## Further reading

There's some Já-specific documentation on [adding a service to Kubernetes](https://jahf.sharepoint.com/sites/taeknisvid/knowledgebase/Add%20service%20to%20Kubernetes.aspx) and [other miscellaneous Kubernetes notes](https://jahf.sharepoint.com/sites/taeknisvid/knowledgebase/Kubernetes%20notes.aspx) on Sharepoint.

- [The Illustrated Children's Guide to Kubernetes](https://cdn.chrisshort.net/The-Illustrated-Childrens-Guide-to-Kubernetes.pdf)
- [What is Kubernetes? Container orchestration explained](https://www.infoworld.com/article/3268073/kubernetes/what-is-kubernetes-container-orchestration-explained.html)
- [What is Kubernetes? An introduction to the wildly popular container orchestration platform](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [What is Kubernetes?](https://www.redhat.com/en/topics/containers/what-is-kubernetes)
- [Kubernetes by Example](http://kubernetesbyexample.com/)
