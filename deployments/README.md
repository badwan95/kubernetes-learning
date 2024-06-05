# Deployments and Rollouts

## Deployment

- When you are creating a deployment, you can roll it by something called "Rolling Uupdate" which means that it will update one pod at a time.

Deployment Strategies:

1. Recreate (Destroy all pods, and create them again), this might lead to downtime and its not the default deployment strategy.
2. Rolling Update (default, updates one pod at a time).

The values are `rollingUpdate: Recreate or RollingUpdate`.

- To update a deployment, you can use `kubectl apply`, but you can also update images using: `kubectl set image deployment/<name> nginx-container=nginx:1.9.1`.

## Rollout (Rolling back)

Check status by running `kubectl rollout status deployment/<name>`.
Check history / revisions by running `kubectl rollout history deployment/<name>`.

To revert to a previous version (revision) use `kubectl rollout undo deployment/<name>`.

To revert to a specific revision, add `--to-revision=<revision-number>` flag to the command above.
