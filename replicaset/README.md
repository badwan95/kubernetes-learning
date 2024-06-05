# ReplicaSet and ReplicationController

- Replicaset is newer, and should always be used if available.
- Main difference is the selectors, in replicaset, it is required, while its optional in replicationcontroller.

You usually do not need to create these manually, as they are a part of the deployment.
