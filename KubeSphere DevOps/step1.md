ks-devops is a pluggable KubeSphere component that can be installed via helm or [ks](https://github.com/kubesphere-sigs/ks/)

## Installing ks-devops via helm
1.First, add helm chart repo:
`helm repo add ks-devops https://kubesphere-sigs.github.io/ks-devops-helm-chart/`{{execute}}

2. Install ks-devops via:
```
kubectl create namespace kubesphere-devops-system 
helm install ks-devops ks-devops/ks-devops -n kubesphere-devops-system \
--set image.pullPolicy=Always --set jenkins.ksAuth.enabled=true
```{{execute}}