### Minimal Installation

1.Install kubesphere ks-installer.
```
kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.1.1/kubesphere-installer.yaml
kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.1.1/cluster-configuration.yaml
```{{execute}}

2.verify kubesphere installation with `kubectl get pods -n kubesphere-system`{{execute}}

3.inspect the installation logs.

```
kubectl logs -n kubesphere-system $(kubectl get pod -n kubesphere-system -l app=ks-install -o jsonpath='{.items[0].metadata.name}') -f
```{{execute}}

4.When all Pods of KubeSphere are running, it means the installation is successful. Check the port (30880 by default) of the console service by the following command. Then you can acces [the console](https://[[HOST2_SUBDOMAIN]]-30880-[[KATACODA_HOST]].environments.katacoda.com) with the default account `admin/P@88w0rd`.

