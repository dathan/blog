---
title: "Automatic Cert Rotation for Gke"
date: 2021-12-29T09:17:19-08:00
draft: false
---


# Why?

My config setup is the following, a free-ish version of GKE autopilot, and a load balancer is my ingress. I want the load balancer to terminate TLS.

# How

Doing some web surfing I found this [blog post](https://johnclarke73.medium.com/tls-configuration-in-gke-the-really-simple-way-5af7abb0e8e1) and it's literally 

```
git clone https://github.com/GoogleCloudPlatform/gke-managed-certs
cd gke-managed-certs
kubectl apply -f managedcertificates-crd.yaml
kubectl apply -f managed-certificates-controller.yaml

then

kubectl annotate ingress [your-ingress-name] 
networking.gke.io/managed-certificates=mydomain-certificate
```

# UPDATE GKE autopilot changes

As of May 2021 GKE removed 3rd party admission webhooks, now you will need to use 
https://cloud.google.com/kubernetes-engine/docs/how-to/managed-certs

