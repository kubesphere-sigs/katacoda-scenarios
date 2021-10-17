ks-devops is a pluggable KubeSphere component that can be installed via helm or [ks](https://github.com/kubesphere-sigs/ks/)

## Prerequisites
1.Check if there is a default Storage Class in your cluster.`kubectl get sc`{{execute}} 

> No storage Class found in the cluster

```bash
controlplane $ kubectl get sc 
No resources found in default namespace.
```

2.Install openebs storage Class in the cluster  
```
kubectl create namespace openebs
helm repo add openebs https://openebs.github.io/charts
helm repo update
helm install openebs --namespace openebs openebs/openebs --wait 
```{{execute}}

3.Set  openebs as  a default storage Class for the cluster
`kubectl patch storageclasses.storage.k8s.io openebs-hostpath -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'`{{execute}}

4.Check if there is a default Storage Class in your cluster.`kubectl get sc`{{execute}} 

## Installing ks-devops via helm
1.First, add helm chart repo:
`helm repo add ks-devops https://kubesphere-sigs.github.io/ks-devops-helm-chart/`{{execute}}

2.Install ks-devops via:
```
kubectl create namespace kubesphere-devops-system 
helm install ks-devops ks-devops/ks-devops -n kubesphere-devops-system \
--set image.pullPolicy=Always --set jenkins.ksAuth.enabled=true
```{{execute}}

## Install CLI ks via hd
[hd](https://github.com/linuxsuren/http-downloader) is a HTTP download tool.
1.install hd
```
curl -L https://github.com/linuxsuren/http-downloader/releases/latest/download/hd-linux-amd64.tar.gz | tar xzv
mv hd /usr/bin/hd
```{{execute}}

2.Install it via 
`hd install kubesphere-sigs/ks`{{execute}}




