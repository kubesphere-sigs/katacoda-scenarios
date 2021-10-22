## Create a Pipeline via ks
You can interacte with KubeSphere DevOps via CLI.
1.Create A cicd pipline using go template 
`ks pip create  --template java --project default --skip-check -b demo-pipeline`{{execute}}

## Trigger the Pipeline via CLI
1.Trigger the Pipeline using ks
`ks pip run -b -p demo-pipeline -n default`{{execute}}

## Interacte with ks using ks dashboard
1.Use ks pipline dashboard via 
`ks pip dash`{{execute}}

2.You can also see the jobs status in [jenkins console](https://[[HOST2_SUBDOMAIN]]-30180-[[KATACODA_HOST]].environments.katacoda.com)
with the `admin` account 

3.Get your 'admin' user password of Jenkins by running:
```
kubectl get secret --namespace kubesphere-devops-system ks-devops-jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode;echo
```{{execute}}

