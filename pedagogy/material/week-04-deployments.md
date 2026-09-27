# Week 4: Deployments

## Learning objectives

By the end of the week a student can explain replicas, rolling updates, and rollback;
relate a Deployment to the ReplicaSets and Pods it manages; and read a rollout's status
from the command line.

## Lecture notes

A **Deployment** declares a desired state for a set of identical Pods: which image,
how many replicas, and how changes roll out. The Deployment controller does not manage
Pods directly. It creates a **ReplicaSet** for each version of the Pod template, and
the ReplicaSet keeps the requested number of Pods running. A Deployment therefore owns
ReplicaSets, and ReplicaSets own Pods.

**Replicas.** `spec.replicas` is the number of Pods wanted. Raising it adds Pods;
lowering it removes them. The ReplicaSet does the adding and removing.

**Rolling update.** When the Pod template changes, for example a new image tag, the
Deployment creates a new ReplicaSet and shifts Pods from the old one to the new one a
few at a time. Two settings shape the pace: `maxSurge`, how many extra Pods may exist
above the desired count during the change, and `maxUnavailable`, how many may be
missing below it. The defaults are 25 percent each. A rolling update keeps the
application available throughout; the alternative strategy, `Recreate`, stops every
old Pod before starting new ones.

**Rollback.** Each ReplicaSet the Deployment has created is a revision. `kubectl
rollout undo` returns to the previous revision by scaling the old ReplicaSet back up;
`--to-revision` picks an older one. Revisions are kept up to `revisionHistoryLimit`,
ten by default.

**Reading status.** `kubectl rollout status deployment/<name>` follows a rollout until
it completes or stalls. `kubectl get deployment` shows READY (Pods ready over desired),
UP-TO-DATE (Pods on the current template), and AVAILABLE. A rollout that never
completes usually has Pods failing their readiness probe or an image that cannot be
pulled; `kubectl describe deployment` and the ReplicaSet's events say which.

## Common misconceptions

- A Deployment restarts a Pod when it changes. It does not; it creates new Pods under a
  new ReplicaSet and removes the old ones.
- Scaling a Deployment creates a new revision. It does not; only a template change does.
- `kubectl rollout undo` deletes the failed version. It does not; the ReplicaSet stays,
  at zero replicas, as a revision you can return to.

## Lab

Deploy an image, scale to three, change the image tag and watch the rollout, break the
image tag on purpose and watch it stall, undo it.
