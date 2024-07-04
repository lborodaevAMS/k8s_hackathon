---
title: ⎈ Kubernetes namespaces bypass
sidebar_label: Welcome
sidebar_position: 2
description: Bypass Kubernetes Namespace from Kubernetes pod to gain access to the cluster - Kubernetes Goat Scenario 🚀
slug: kubernetes-namespaces-bypass-from-kubernetes-cluster-pod/welcome
---

# ⎈ Kubernetes namespaces bypass

## 🙌 Overview

Woah! this is a big misconception in the Kubernetes world. Most people assume that when there are different namespaces in Kubernetes and resources are deployed and managed they are secure and not able to access each other. Many real-world multi-tenant environments are getting exploited and critical resources are exposed internally due to this. By default, Kubernetes comes with flat networking schema and if we need to have segmentation then we have to create them by creating certain boundaries like NSP (network security policies) and others. In this scenario, we see how we can bypass the namespaces and access other namespaces resources.

![](../images/scenario-11.png)

By the end of the scenario, we will understand and learn the following

1. You will understand the misconception of the Kubernetes namespaces
2. Learn about the Kubernetes networking flat schema and communicating across namespaces
3. Performing the reconnaissance and testing for the network port scanning and vulnerabilities
4. Gaining access to other namespaces resources bypassing the namespaces restrictions

### ⚡️ The story

By default, Kubernetes uses a flat networking schema, which means any pod/service within the cluster can talk to others. The namespaces within the cluster don't have any network security restrictions by default. Anyone in the namespace can talk to other namespaces. We heard that Kubernetes-Goat loves cache. Let's see if we gain access to other namespaces

:::info

- To get started with the scenario, let's run our awesome `hacker-container` in the default namespace

```bash
kubectl run -it hacker-container --image=madhuakula/hacker-container -- sh
```

:::

![Scenario 11 Welcome](../images/sc-11-1.png)

### 🎯 Goal

:::tip

Gain access to the `cache-store` and obtain the `k8s_goat_flag` flag value to complete this scenario.

:::

### 🪄 Hints & Spoilers

<details>
  <summary><b>✨ Don't see other services? </b></summary>
  <div>
    <div>Let's go back to the old school port scanning, but with <b>zmap</b> with entire cluster range for redis port 🙌</div>
  </div>
</details>

<details>
  <summary><b>✨ Found cache-store service? </b></summary>
  <div>
    <div>Now it's time to read redis docs and get the <b>SECRETSTUFF</b> key 🎉</div>
  </div>
</details>


## 🔖 References

- [Kubernetes Namespaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)
- [Kubernetes Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
