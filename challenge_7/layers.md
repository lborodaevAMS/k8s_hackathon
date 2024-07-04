---
title: ⎈ Hidden in layers
sidebar_label: Welcome
sidebar_position: 2
description: Analyze hidden layers in Container in Kubernetes Cluster - Kubernetes Goat Scenario 🚀
slug: hidden-in-container-layers-in-kubernetes-cluster/welcome
---

# ⎈ Hidden in layers

## 🙌 Overview

Most of the container images download and used on the internet are created by someone else. If we don't know how they get created (which means if we don't have `Dockerfile`) then I think we might be in trouble sometimes. In this scenario, we can see how to analyze the docker container image layers by using the built-in utilities and also some popular open-source utilities like dive to understand the container image layers.

![](../images/scenario-diagram-wip.png)

By the end of the scenario, we will understand and learn the following

1. How to explore, introspect and analyze docker container images
2. Using open source tools like dive to perform container image analysis
3. Able to work with standard command-line utilities

### ⚡️ The story

Sensitive information disclosure is one of the most common vulnerabilities existing in the wild. Mishandling of passwords, private keys, tokens, etc in the containerization world is easy. Here in this scenario, we will analyze and identify one of such mishandled bad practices that leads to sensitive information disclosure.

:::info

- To get started with the scenario, run the following command and explore the `hidden-layers` job

```bash
kubectl get jobs
```

:::

![Scenario 15 get jobs](../images/sc-15-0.png)

### 🎯 Goal

:::tip

Find the `k8s_goat_flag` flag value in one of the hidden layers of the container, then you have completed this scenario.

:::

### 🪄 Hints & Spoilers

<details>
  <summary><b>✨ Still trying to understand layers? </b></summary>
  <div>
    <div>Explore the default commands like <b>docker history</b>, also popular utilities like <b>dive</b> 🙌</div>
  </div>
</details>

<details>
  <summary><b>✨ Want to get the flag? </b></summary>
  <div>
    <div>We can use <b>docker save</b> command to export the container as a archive file and we can do analysis of each layer 🎉</div>
  </div>
</details>


## 🔖 References

- [Digging into docker layers](https://jessicagreben.medium.com/digging-into-docker-layers-c22f948ed612)
- [dive](https://github.com/wagoodman/dive)
