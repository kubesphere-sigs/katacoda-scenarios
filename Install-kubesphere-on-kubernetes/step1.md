In addition to supporting deploying on VM and BM, KubeSphere also supports installing on cloud-hosted and on-premises existing Kubernetes clusters.

## Prerequisites

> - Kubernetes Version: 1.17.x, 1.18.x, 1.19.x, 1.20.x;
> - CPU > 1 Core, Memory > 2 G;
> - An existing default Storage Class in your Kubernetes clusters.

1.Make sure your Kubernetes version is compatible by running `kubectl version`{{execute}} in your cluster node.
> Pay attention to `Server Version` line, if `GitVersion` is greater than `v1.17.0`, it's good to go

2.Check if the available resources meet the minimal prerequisite in your cluster.
`kubectl describe nodes/node01 | grep --color=always  "memory:" | tail -1 `{{execute}}

3.Check if there is a default Storage Class in your cluster.`kubectl get sc`{{execute}} 

> No storage Class found in the cluster

```bash
controlplane $ kubectl get sc 
No resources found in default namespace.
```

4.install openebs storage Class in the cluster  
```
kubectl create namespace openebs
helm repo add openebs https://openebs.github.io/charts
helm repo update
helm install openebs --namespace openebs openebs/openebs --wait 
```{{execute}}

5.set  openebs as  a default storage Class for the cluster
`kubectl patch storageclasses.storage.k8s.io openebs-hostpath -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'`{{execute}}

6.Check if there is a default Storage Class in your cluster.`kubectl get sc`{{execute}} 

If your Kubernetes cluster environment meets all requirements mentioned above, then you can start to install KubeSphere.
