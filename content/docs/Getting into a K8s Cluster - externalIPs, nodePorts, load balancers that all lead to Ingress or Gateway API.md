
---
title: "Getting into a K8s Cluster - externalIPs, nodePorts, load balancers that all lead to Ingress or Gateway API"
date: 2024-05-04T17:21:33Z
lastmod: 2025-12-07T23:45:20Z
categories: ['kubernetes', 'cilium']
draft: false
---


# Getting into a K8s Cluster - externalIPs, nodePorts, load balancers that all lead to Ingress or Gateway API

The tl;dr is that if you want to get external access you need to get an IP to forward traffic. This can be separate, or using a load balancer service.

## externalIPs
https://kubernetes.io/docs/concepts/services-networking/service/#external-ips
```
externalIPs:
    - 198.51.100.32
```
Is added to your service definition.

Kubernetes does NOT manage these IPs or the routing for this. The assumption is that this IP is on a node in the cluster.

This can work well with only a handful of IPs and tight coupling between the cluster and applications.
## nodePort
https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport

A port available on all nodes can be used.
Eg. http://my-k8s-node.domain:31234

```
spec:
  type: NodePort
  selector:
    app.kubernetes.io/name: MyApp
  ports:
    - port: 80
         # By default and for convenience, the Kubernetes control plane
      # will allocate a port from a range (default: 30000-32767)
      nodePort: 30007
```

## Load Balancers
Use a cloud based load balancer to get traffic in.
Alternatively you can leverage MetalLB, PureLB, or Porter
### MetalLB
Either L2 mode or BGP mode. Needs a controller, and a speaker to configure nodes.
### PureLB
For fun - it can hook into Netbox to get info for IPAM.
### Cilium L2 LB
Baked right into Cilium.

## Ingress
Ingress requires Ingress Controllers. Ingress Controllers do **not** manage the IPs - they are configured to use externalIPs, nodePorts, or load balancers to get the traffic to the Ingress Controller.

## Gateway API
Gateway API is a replacement/evolution of Ingress. While Ingress was HTTP only in design, Gateway API is less specific.

The Gateway API spec is also about including items like Service Mesh - it also means that instead of a separate Ingress Controller you can leverage your CNI.

https://cilium.io/use-cases/gateway-api/

<!-- #public #kubernetes #cilium -->

<!-- {BearID:A8C5A668-0A98-4285-9F50-0D9824FC4ABA} -->
