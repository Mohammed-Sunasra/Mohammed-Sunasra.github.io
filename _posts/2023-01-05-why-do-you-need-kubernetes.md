---
layout: post
title: Why do we need Kubernetes?
comments: true
excerpt: Let's try to understand what Kubernetes is, why do we really need Kubernetes, and what Kubernetes is NOT before we dive deeper into what exactly is Kubernetes and how it works.
---

## What is Kubernetes

I am sure we all have heard a lot of things about Kubernetes from quite some time now and wondering what is it? So first things first, let's try to define what exactly is Kubernetes.

- [Kubernetes](https://kubernetes.io/docs/concepts/overview/), also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications. Think about it like a tool to monitor, manage, scale a lot (tens of thousands) of container based applications.
- For now, just stick to this definition until we dive much deeper into why do we need it, what is the architecture and the different components it uses to manage the applications.

## Why do we need Kubernetes?

Docker is a great way to package your applications into small, lightweight containers and move them around without worrying too much about the code and the required dependencies. But it becomes really difficult to manage more and more containers at scale when you are experiencing heavy traffic, and you have a distributed architecture in place. Below are some of the reasons that highlight why we may need something like Kubernetes to manage our containers

### Fault tolerance

What happens when a container crashes due to any reason and new containers needs to be started immediately without disturbing the user traffic. This requires some sort of monitoring in place first which will send some alert and new containers needs to be spawned up in no downtime whatsoever.

This manual monitoring and spinning up of new containers is not fault-tolerant and may result in downtime or other issues. With Kubernetes, it makes sure that there are always a certain number of pods/containers running at all times and if a pod/container dies, it will automatically spin up a replacement pod, making sure the current state of the system always matches with the desire state.

Kubernetes also has ways to track what were the changes made to your deployments and, if required, it can also help you do rollbacks with just a single line of command.

### Scale and discovery

Suppose you were working with a single container till the time the traffic was manageable, until there comes a point where we need to add more instances of the same container. Since both the containers cannot listen on the same port, they need to listen to different ports.

The problem with this now is how do you make sure we manage the workload so that both the containers are serving the requests and the load balancer distributes the traffic to both the containers. This is manageable using bare bone containers but requires a lot of management of ports, load balancing etc.

With Kubernetes, you just specify how many replicas of the container(pods) you may require, and Kubernetes will make sure there are a same number of pods running all the time.
If we experience more traffic at any point, it only a matter of adding more workers (think virtual machines) and replicas, and the traffic is handled and distributed without any trouble.

### Distributed

Kubernetes works in a distributed setting where it can have multiple master nodes and multiple worker nodes. The master nodes mostly takes care of monitoring the state of the overall system and the worker nodes takes care of managing the containers.

If at any point in time, we may need more hardware, then it's just a matter of adding more machines/nodes and Kubernetes will take of distributing the workload among them.
We can also have heavy machines for specific workloads and inform Kubernetes how many resources our containers needs. Kubernetes can then fit the containers onto your nodes to make the best use of your resources. This is helpful for managing heavy workloads like training machine learning models on GPU nodes

### Platform/Cloud Agnostic

There are cloud based services like AWS ECS (Elastic container service) which, given your containers, manages the backend infrastructure (compute, network, storage) for you. The problem with such services is they lock you into their own cloud ecosystem, requires you to learn how to operate those specific services and have a very small community.

Kubernetes on the other hand is open source which gives you the freedom to take advantage of on-premises, hybrid, or public cloud infrastructure, letting you effortlessly move workloads to where it matters to you.

### More Features

Above are only some of the reasons where Kubernetes can help. It also has much more features like

1. Secret and config management
2. Automatic distribution
3. Path based routing
4. Health checks
5. Persisting data volumes
6. Integration with other technologies like Prometheus(for logging), ArgoCD(for GitOps),

## What Kubernetes is not?

- It’s also not an alternative to Docker but a technology which works on top of container based technologies like Docker
- It’s not a specific service provided by a cloud provider. The same technology can be used anywhere on any cloud or on-premise
- It’s not a paid service. It’s open source. Managed services built on top of Kubernetes like AKS, EKS etc. are of course paid.

## Conclusion

I hope the above points helped you understand what is Kubernetes, why do we need Kubernetes and what Kubernetes is not. In the subsequent articles, I'll try to dive deeper into Kubernetes, how it works, what is the architecture and the different components and tooling around Kubernetes
