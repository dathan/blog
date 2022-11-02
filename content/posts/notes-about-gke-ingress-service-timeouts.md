---
title: "Notes About Gke Ingress Service Timeouts"
date: 2022-11-02T10:07:11-07:00
draft: false
---



## Problem

 GKE for all backend services has a default timeout of 30 seconds for a response from the backend or the service. If the request takes more than 30 seconds a 502 Bad Gateway occurs and the message
 


`Error: Server Error
 The server encountered a temporary error and could not complete your request.
 Please try again in 30 seconds.`


 ## Context

 The problem is summarized as timeouts that need to be configured for the load balancer, but how do you do that?


 ## Solution

 After some googling, I found that this [link](https://cloud.google.com/kubernetes-engine/docs/how-to/ingress-features) has the answers I am looking for. In summary, to set timeouts for your service from the load balancer, we need to create a CR of `BackendConfig`, then in the service reference that config much like this example 

 `cloud.google.com/backend-config: '{"ports": {"80":"my-backendconfig"}}'` 

 as an annotation for the service.


 ## Conclusion

 At least there is a way. I wish there was something more straight forward like back in the days with PHP to prevent infinate loops, just wait forevery globally or let the server crash.



