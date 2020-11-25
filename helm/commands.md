# Helm 2 to 3 migration commands
* Installing plugin
``` 
helm3 plugin install https://github.com/helm/helm-2to3
```

# HELM-3 commands
* To install helm chart
  helm install -f myvalues.yaml myredis ./redis
  or helm install --set name=prod myredis ./redis
  or helm install --set-string long_int=1234567890 myredis ./redis
  or helm install --set-file my_script=dothings.sh myredis ./redis
  
* To install helm charts on specific namespace
  helm install -f myvalues.yaml myredis ./redis -n nemespace_name
  
  we can pass multiple values.yaml or --set , but which is the rightmost will have the precedance
  helm install -f myvalues.yaml -f override.yaml  myredis ./redis
  
* Dry-run
  helm install -f myvalues.yaml myredis ./redis --dry-run
  
* To delete helm chart
  helm uninstall release_name
  helm uninstall release_name --dry-run
  helm uninstall release_name -n namespace_name (To delete helm chart which was installed on specific namespace)
  
* To list the installed charts
  helm list
  helm list -n namespace_name (To list installed helm charts on specific namespace)
  
* To timeout the helm install command
  helm install -f values.yaml test . -n cnf --timeout 20s  (Default is 5 minutes if we didnt pass the --timeout parameter)
  
* To get the config file(manifest) which we used during helm install
  helm get manifest release_name
  helm get manifest reease_name -n namespace_name

* To add a helm chart repo
  helm repo add [NAME] [URL] [flags]
  helm repo add bitnami https://charts.bitnami.com/bitnami
  
  helm repo add - add a chart repository
  helm repo index - generate an index file given a directory containing packaged charts
  helm repo list - list chart repositories
  helm repo remove - remove one or more chart repositories
  helm repo update - update information of available charts locally from chart repositories
  
* To search helm charts in that repo
  helm search repo repo-name (eg. helm search repo bitnami/)
  To search for mongodb chart hem search repo bitnami/mango
  
  
# HELM-2
