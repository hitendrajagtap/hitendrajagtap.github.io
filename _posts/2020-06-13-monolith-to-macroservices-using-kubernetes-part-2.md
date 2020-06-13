---
layout: post
title: "Monolith to Macroservices using Kubernetes - Part 2"
date: 2020-06-13 09:00:00 +1030
description: Breaking a Monolith into Macroservices using Kubernetes - Part 2.
img: monolith-to-macroservices-kubernetes.jpg
categories:
  - containers
tags:
  - monolith
  - macroservices
  - kubernetes
  - containers
---
This post is in continuation of the previous part:

[Monolith to Macroservices using Kubernetes - Part 1]({% post_url 2020-05-27-monolith-to-macroservices-using-kubernetes-part-1 %})

## Breaking the Monolith

In the previous part we had a monolith with a N-tier architecture. There were multiple services being called from the presentation layer in order to deliver a package via drone. The problem with such an architecture is that it is highly coupled and difficult to scale. In this post I have extracted the services into couple of main macroservices that are decoupled and containarised.

## Macroservices using Kubernetes

The monolith is now broken into 2 macroservices - a PackageProcessor service which creates the package to be delivered from the order, and a DroneScheduler service which manages the drones for the delivery. The DroneScheduler macroservice can first identify the drone that is available for delivery and then can despatch the drone once the package is ready to be delivered. Of course, the macroservices currently have dummy implementations, but we are not far from seeing these services in real life!

<p align="center">
  <img src="/assets/img/macroservices.jpg" alt="Macroservices" />
</p>

The front-end of the application orchestrates the calls to these macroservices. The final code for this application after being broken into macroservices in available in `src/after` folder of the repository <https://github.com/hitendrajagtap/monolith-to-macroservices-using-kubernetes>. I have used Helm charts here to create the Kubernetes deployments. These macroservices can be deployed locally or to your choice of Kubernetes cluster on a cloud service. Happy hacking!
