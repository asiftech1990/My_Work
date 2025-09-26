Pod logs → Node filesystem → Fluentd/Filebeat (DaemonSet) → Elasticsearch → Kibana

Log Collection (Fluentd / Fluent Bit / Filebeat as DaemonSet)

Log Storage (Elasticsearch)

Visualization (Kibana)

Pod runtime data & volumes → /var/lib/kubelet/pods/
Container images & layers → /var/lib/containers/storage/
/var/log/containers/ → symlinks to container logs (organized per pod & container).
/var/log/pods/ → pod-specific log files.

Overlay → container writable layers (managed by CRI-O and OverlayFS).

tmpfs → in-memory file systems for things like /run, /tmp, pod ephemeral storage.

Layer	Role
lower	Base image layers (read-only)
diff	Upper layer (writable, container-specific)
merged	Combined view seen by the container
work	Temporary workspace for OverlayFS


argocd-server

Provides the web UI and API.

 argocd-repo-server

Communicates with Git repositories.

Pulls manifests, renders Helm/Kustomize charts, and provides them to the controller.

3️⃣ argocd-application-controller

Core controller that monitors Applications.

Compares desired state in Git with actual state in OpenShift.

Triggers syncs, pruning, and rollout of resources.

4️⃣ argocd-dex-server (optional)

Provides SSO / OIDC authentication.

5️⃣ argocd-redis

Stores temporary state, caching, and session info.

================================

Internet gatewat

Create Internet gateway attach to VPC.
Create 2 routes public and private and associate to public and private subnet
Edit public route and create rule to allow all traffic using internet gateway

NAT instance = openshift internet access from private instance

=========

Installation/adding nodes
Application onboarding
capacity planning (resource quota/limit ranges)
taint toleration
upgrade
mc/mcp
GITOPS Argo
vendor operators
storage
Application troubleshooting
Vulnerablities 
Vendor components (Dynatrce/logscale/sysdig)

==================================

1- Image pullback
2- File system issue (dmesg)
3- Latency issue
4- Hardnening (node reboot)
5- Upgrade odf issues
6- disk full issue
7- Pods scheduling 
8- Health check issue





