 kubectl create -f ns.yaml
 kubectl get all -n wordpress
 kubectl create -f secret.yaml
 kubectl describe secret/db-secret -n wordpress
 kubectl create -f pvpvc.yaml
 kubectl create -f pvpvcwp.yaml
 kubectl create -f dbdepsvc.yaml
 kubectl get svc -n wordpress
 kubectl get ep -n wordpress
 kubectl get po -n wordpress
 kubectl create -f phpdepsvc.yaml
 kubectl get svc -n wordpress
 kubectl create -f wordpressdepsvc.yaml
 kubectl get all -n wordpress
