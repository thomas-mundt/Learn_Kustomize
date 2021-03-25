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

