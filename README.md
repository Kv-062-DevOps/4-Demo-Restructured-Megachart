# 4-demo
Charts,Depleyments,ELK
* Read ecr.md
* Before deploy we should create specific namespace name (as new deployment name)
```  kubectl create namespace name_offuture_deploy ```
* Create deploy 
``` helm install --set region="dynamodb-region" --set secret_key="dynamodb-secret-key" --set access_key="dynamodb-access-key" deploy-specific-name ./back ```
* Check
```  kubectl get all -n namespace ```
*Install Traefik
``` helm install traefik stable/traefik --set dashboard.enabled=true,dashboard.domain=traefik.cluster.local,rbac.enabled=true  --namespace kube-system ```
or you can set via values-traefik.yaml
``` helm install --values values.yaml stable/traefik ```
Remember to reuse command for getting LB address (to check service in the future)
values.yaml you can find by this link https://github.com/helm/charts/tree/master/stable/traefik
*You can deploy with trhee different ingress configuration: by percent(canary), by replica num(canary), by redirection path(versioning by path)
``` helm install --set region="dynamodb-region" --set secret_key="dynamodb-secret-key" --set access_key="dynamodb-access-key" deploy-specific-name ./back-...  ```
*Check out via Service Load Balancer address and dashboard configuration
``` kubectl port-forward service/traefik-dashboard 8083:80 -n kube-system ```
Go to browser 127.0.0.1:8083 address


