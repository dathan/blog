---
title: "Tailscale Kubernetes"
date: 2021-10-13T17:33:37-07:00
draft: true
---

Last year I wrote a quick [docker image and helm chart](https://github.com/dathan/tailscale-docker) to install tailscale into your Kubernetes cluster. My particular use case was reaching devices between multiple colliding networks from the cloud to a physical location someplace around the world. Tailscale is perfect for this use-case, and putting together that project was fun and informative. 

Today I read this [post](https://tailscale.com/blog/kubecon-21/) by [Maisem Ali](https://twitter.com/maisem_ali) and [Maya Kaczorowski](https://twitter.com/MayaKaczorowski). A fantastic combination of features and abilities that make reaching services in a Kubernetes cluster easy. I am looking forward to testing some of the features and possibly adding some options to reach things behind the Kubernetes cluster.