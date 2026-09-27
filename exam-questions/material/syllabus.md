# Introduction to Kubernetes: syllabus

A twelve-week undergraduate course. One lecture and one lab per week. Prerequisites:
a programming course and familiarity with the command line. Assessment: weekly labs,
a midterm after week 6, a final project.

| Week | Topic | Learning objectives |
|---|---|---|
| 1 | Containers | Build an image, run a container, explain what a namespace and a cgroup isolate. |
| 2 | Why orchestration | State the problems a scheduler solves; describe a cluster's control plane and nodes. |
| 3 | Pods and Services | Write a Pod manifest; expose it with a Service; explain labels and selectors. |
| 4 | Deployments | Explain replicas, rolling updates, and rollback; relate a Deployment to its ReplicaSets and Pods; read a rollout's status. |
| 5 | Configuration | Use ConfigMaps and Secrets; explain why configuration is separate from images. |
| 6 | Storage | Distinguish a volume, a PersistentVolume, and a claim; explain StorageClasses. |
| 7 | Networking | Trace a request through a Service and an Ingress; explain cluster DNS. |
| 8 | Scheduling | Use requests, limits, taints, tolerations, and affinity; predict where a Pod lands. |
| 9 | Extending Kubernetes | Explain Custom Resources and operators; read a controller's reconcile loop. |
| 10 | Observability | Read logs, metrics, and events; explain readiness and liveness probes. |
| 11 | Security | Explain RBAC, ServiceAccounts, and NetworkPolicies; apply least privilege to a workload. |
| 12 | Delivery | Describe GitOps; explain how a commit becomes a running change. |

Question levels: weeks 1 to 4 test recall and explanation; weeks 5 to 8 add applying a
concept to a manifest; weeks 9 to 12 add reasoning about a system's behaviour.
