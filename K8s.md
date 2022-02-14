# K8s

**Get images inside pods from specific namespace**
> For single pod, remove ``.items[*]``
```
kubectl get pods -n <namespace> -o jsonpath="{.items[*].spec.containers[*].image}" |\
tr -s '[[:space:]]' '\n' |\
sort |\
uniq -c
```

**Get the configuration yaml for a service/deployment**
```
kubectl get all -n <namespace>
kubectl get -n <namespace> <service/deployment name> -o yaml
```

**Use rollout to restart the deployment**

``kubectl rollout restart deployment <deployment_name> -n <namespace>``