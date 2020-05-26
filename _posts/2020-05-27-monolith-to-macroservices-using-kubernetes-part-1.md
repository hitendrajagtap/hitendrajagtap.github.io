---
layout: post
title: "Monolith to Macroservices using Kubernetes - Part 1"
date: 2020-05-27 09:00:00 +1030
description: Breaking a Monolith into Macroservices using Kubernetes - Part 1.
img: monolith-to-macroservices-kubernetes.jpg
categories:
  - containers
tags:
  - monolith
  - macroservices
  - kubernetes
  - containers
---
Traditionally, enterprise software systems had been built as one giant monolith due to various limitations. With the advent of cloud technologies and the need for companies to be agile, it has become possible to break the monoliths into manageable, smaller services. These distributed systems interact with each other to achieve common business goals.

## Why Macroservices?

Many companies begin modernising their applications by breaking the monolith, however, directly into microservices. In this way, 100s of microservices are required to cover the functionality of the complete monolith. Along with the advantages of microservices, there are many challenges as well. I might have to write another blog post to elaborate on this. Sometimes, if a few services need to be extracted from the monolith, then a "strangler pattern" can be used.

Macroservices on the other hand, are comparatively larger services. Few macroservices should be sufficient to perform the functionalities of the complete monolith. Macroservices have some advantages and are suitable as an intermediate step for various reasons for companies moving towards modernising their applications. I shall cover the advantages and disadvantages of macroservices in another blog post.

The focus of this blog post is more practical, technical, and hands-on. Here, I have taken a monolith example and shown how it can be broken into a few macroservices using Kubernetes container technology.

## The Monolith

The example monolith that I have used here is a hypothetical drone delivery application described in one of Microsoft Learn samples <https://docs.microsoft.com/en-us/learn/modules/microservices-architecture/>. I have forked the original monolith source code and modified it at <https://github.com/hitendrajagtap/monolith-to-macroservices-using-kubernetes>.

<p align="center">
  <img src="/assets/img/monolith.jpg" alt="The Monolith" />
</p>

The monolith is a traditional n-tier architecture application. The monolith source code is in the <i>src/before</i> folder. When a drone delivery is requested, the request processor orchestrates the request. It first packages the delivery in the package-processor service and then schedules the delivery using drone-scheduler service. Both these services are in the services layer of the monolith.

## Breaking into Macroservices

As we have seen above, there are 2 distinct services which can be de-coupled from the monolith - the package-processor service and the drone-scheduler service. In Part 2 of this blog post, I shall demonstrate with code how these 2 services can be containerised and deployed in a Kubernetes cluster. Also, I shall show how our Drone-Delivery will be orchestrated. Until the next part, please feel free to peruse through the source code of the application given above and be ready for the next generation delivery service!

---
