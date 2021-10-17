## Create a Pipeline via ks
You can interacte with KubeSphere DevOps via CLI.
1.Create A cicd pipline using go template 
`ks pip create --ws simple --template go --project katacoda --skip-check -b pipeline`{{execute}}

## Trigger the Pipeline via CLI
1.Trigger the Pipeline using ks
`ks pip run`{{execute}}

## Interacte with ks using ks dashboard
Use ks pipline dashboard via 
`ks pip dash`{{execute}}

