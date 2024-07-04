---
title: ⎈ DoS the Memory/CPU resources
sidebar_label: Welcome
sidebar_position: 2
description: Denial of Service (DoS) of Memory and CPU resources in Kubernetes Cluster and Containers - Kubernetes Goat Scenario 🚀
slug: denial-of-service-memory-and-cpu-resources-in-kubernetes-cluster/welcome
---

# ⎈ DoS the Memory/CPU resources

## 🙌 Overview

Availability is one of the triads in CIA. One of the core problems solved by Kubernetes is the management of the resources like autoscaling, rollouts, etc. In this scenario, we will see how attackers can leverage and gain access to more resources or cause an impact on the availability of the resources by performing the DoS (Denial of Service) if there were no resource management configurations implemented on the cluster resources like memory and CPU requests and limits.

![](../images/scenario-diagram-wip.png)

By the end of the scenario, we will understand and learn the following

1. Learn to perform the DoS on computing and memory resources using `stress-ng`
2. Understand the Kubernetes resources management for pods and containers
3. Explore the Kubernetes resource monitoring using the metrics and information 

### ⚡️ The story

There is no specification of resources in the Kubernetes manifests and no applied limit ranges for the containers. As an attacker, we can consume all the resources where the pod/deployment running and starve other resources and cause a DoS for the environment.

:::info

To get started with the scenario, navigate to [http://127.0.0.1:1236](http://127.0.0.1:1236)

:::

![Scenario 13 Welcome](../images/sc-13-1.png)

### 🎯 Goal

:::tip

Access more resources than intended for this pod/container by consuming 2GB of memory to successfully complete the scenario.

:::

### 🪄 Hints & Spoilers

<details>
  <summary><b>✨ How can I DoS resources? </b></summary>
  <div>
    <div>You can leverage the popular command line utility like <b>stress-ng</b> 🙌</div>
  </div>
</details>


## 🔖 References

- [Resource Management for Pods and Containers](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers)
