# kubernetes-learning

Learning notes and files for kubernetes

## General Data

- You can get the status of many kubernetes components by running `kubectl get <component>`, add `-o <type, such as json>` for the output to be different style.
- To check if a command or file work as expected without executing the command/file, add the flag `--dry-run=client`.

## Imperative commands

- To create a pod with an image, do `kubectl run <podname> --image=<image-name>`.
- There are some flags you can use, such as: `--labels=key1=value1,key2=value2`, `--port=5432`.

- To generate a file quickly without typing it from scratch, you can use this command `kubectl run nginx --image=nginx --dry-run=client -o yaml > <file-name>.yaml`, you can do that for deployment as well, with `kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > <deployment-file>.yaml`.

## Namespaces

Namespaces are used to isolate resouces, for example we might have 3 namespaces (dev, testing and prod).
You can have different set of policies for each one, for example dev and testing would have limited resources compared to prod.

There are some default 4 namespaces:

1. kube-system
2. kube-public
3. kkube-node-lease
4. default

For resources inside the same namespace, they can refer to eachother by their names, but it can also connect to resources from another namespace, but they must append the namespace first `servicename.namespace.svc.cluster.local`, while in the same namespace, just the `servicename` is enough.

The `cluster.local` is the default domain name for the kubernetes cluster.

- To get resources from another namespace, use the flag `--namespace=<name>`.
- To create a resource in a namespace, you can use `--namespace` flag, or add `namespace=name` to the manifest file itself.
- To create a new namespace, you can create a manifest file, or use `kubectl create namespace <name>`.
- To switch the namespace, use `kubectl config set-context --current --namespace=<name>`, also `kubectl config set-context $(kubectl config current-context) --namespace=<name>`.
- To check the current namespace, use `kubectl config get-contexts`.

You can create a **resource quota** for a namespace by creating a file.
