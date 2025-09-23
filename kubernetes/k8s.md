**Q: Which component is responsible for Pod_IP & Service_IP**

| IP_TYPE      | Assigned By        | Componet Involved 
|--------------|--------------------|----------------------------
| Pod_IP       | CNI Plugin         | CNI (calico/flannel )   
| Service_IP   | K8s control plane  | kube-controller + kube Proxy   
        
**Q: What's the difference betwneen kube-proxy and CNI**

Kube-proxy vs CNI in Kubernetes

Overview
kube-proxy and CNI (Container Network Interface) are distinct components that handle different layers of Kubernetes networking:

CNI: Provides basic Pod-to-Pod connectivity (network foundation)

kube-proxy: Manages service discovery and load balancing (service abstraction)

|Feature          |	CNI Plugin                                                  |	Kube-Proxy
|-----------------|-----------------------------------------------------------------|--------------------------------------------------------------------
|Primary Role	 | Basic network connectivity for Pods                               |	Service abstraction and load balancing
|Core Function	 | Assigns IP addresses to Pods; enables cross-node Pod communication |   Translates Service IPs to backend Pod IPs; implements load balancing
|What It Manages | Pod IPs, network interfaces, routing, network policies            |	Network rules (iptables/IPVS) for Service traffic routing
|Analogy	 | Building roads and assigning addresses                             |	Traffic light and sign system for Services
|Examples	 | Calico, Flannel, Cilium, AWS VPC CNI	                            |   Kubernetes component running on every node

**How They Work Together :**

Pod A tries to communicate with a Service (my-service)

Kube-proxy handles Service IP translation (ClusterIP → Pod IP)

CNI handles the actual packet routing between nodes if Pods are on different nodes
