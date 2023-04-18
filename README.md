# Learn Kustomize

## Links

- https://kubectl.docs.kubernetes.io/references/kustomize/kustomization/



```
kustomize build .
kustomize build . | kubectl apply -f -
# or
kubectl create --kustomize .
kubectl create -k .
kubectl delete -k .
kubectl create -k overlays/dev/

```


## Patches



JSON 6902 Patch
```
patches:
  - target:
      kind: Deployment
      name: api-deployment
    patch: |-
      - op: replace
        path: /spec/replicas
        value: 5
```



Strategic merge patch
```
patches:
  - patch: |-
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: api-deployment
      spec:
        replicas: 5
```

Or in seperate file
```
patches:
  - path: replica-patch.yaml
    target:
      kind: Deployment
      name: nginx-deployment
```

replica-patch.yaml
```
- op: replace
  path: /spec/replicas
  value: 5
```
