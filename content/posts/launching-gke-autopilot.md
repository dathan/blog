---
title: "Launching Gke Autopilot"
date: 2021-12-27T12:33:06-08:00
draft: false
---

I am going to launch foreveraward.com on Kubernetes because why not? I need something to manage the foreveraward container and I am good with Kubernetes.

The following checklist is going to be needed.

* Cluster GKE (1st time building)
* Helm3 compatible
* Ingress controller to support the ingress to the react app


## Launching GKE cluster

### Creating a cluster

Using gcloud the command-line tool for Google cloud, let's create a cluster with redundancy in us-west-1

```
gcloud container clusters create-auto foreveraward     --region us-west1     --project=my-platform-11111
```

### Get the cluster credentials

```
gcloud container clusters describe foreveraward --region us-west1
```

Now the kubectl config is written where with the credentials needed to operate with the public cluster.

```
$ helm version
version.BuildInfo{Version:"v3.7.2", GitCommit:"663a896f4a815053445eec4153677ddc24a0a361", GitTreeState:"clean", GoVersion:"go1.17.3"}

~/workspace/blog (main) [gke_handy-platform-336015_us-west1_foreveraward|]
$ helm ls
NAME	NAMESPACE	REVISION	UPDATED	STATUS	CHART	APP VERSION
```

The default k8s cluster information is the following

```
kubectl get pods --all-namespaces
NAMESPACE     NAME                                                     READY   STATUS    RESTARTS   AGE
kube-system   event-exporter-gke-5479fd58c8-jmw68                      2/2     Running   0          34m
kube-system   filestore-node-59xt5                                     3/3     Running   0          34m
kube-system   filestore-node-9bl8s                                     3/3     Running   0          34m
kube-system   fluentbit-gke-fx8dx                                      2/2     Running   0          34m
kube-system   fluentbit-gke-qv5jj                                      2/2     Running   0          34m
kube-system   gke-metadata-server-p6f67                                1/1     Running   0          34m
kube-system   gke-metadata-server-vsxbq                                1/1     Running   0          34m
kube-system   gke-metrics-agent-jxmsf                                  1/1     Running   0          34m
kube-system   gke-metrics-agent-wdtnz                                  1/1     Running   0          34m
kube-system   konnectivity-agent-6f574c9546-4lzbp                      1/1     Running   0          34m
kube-system   konnectivity-agent-6f574c9546-m9czx                      1/1     Running   0          33m
kube-system   konnectivity-agent-autoscaler-5c49cb58bb-tc7g7           1/1     Running   0          34m
kube-system   kube-dns-697dc8fc8b-5cbcp                                4/4     Running   0          34m
kube-system   kube-dns-697dc8fc8b-phfrg                                4/4     Running   0          33m
kube-system   kube-dns-autoscaler-844c9d9448-r8s5r                     1/1     Running   0          34m
kube-system   kube-proxy-gk3-foreveraward-default-pool-1137ba4d-mzg6   1/1     Running   0          32m
kube-system   kube-proxy-gk3-foreveraward-default-pool-424a750d-zcmh   1/1     Running   0          33m
kube-system   l7-default-backend-865b4c8f8b-czg8h                      1/1     Running   0          34m
kube-system   metrics-server-v0.4.4-857776bc9c-sh7wl                   2/2     Running   0          33m
kube-system   netd-gjlqz                                               1/1     Running   0          34m
kube-system   netd-k2z5x                                               1/1     Running   0          34m
kube-system   node-local-dns-m7dmp                                     1/1     Running   0          34m
kube-system   node-local-dns-mvdxw                                     1/1     Running   0          34m
kube-system   pdcsi-node-8np2k                                         2/2     Running   0          34m
kube-system   pdcsi-node-k4zqw                                         2/2     Running   0          34m
```


## Details

More details can be found at GCP's documentation of [GKE Autopilot](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-an-autopilot-cluster)
