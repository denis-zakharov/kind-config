# Create
```
kind create cluster --config=kind-deploy.yml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=180s
```

# Delete
```
kind delete cluster --name=denis
```

# Docs
https://kind.sigs.k8s.io/docs/user/configuration/