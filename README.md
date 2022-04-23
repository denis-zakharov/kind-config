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

# Tools
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod u+x kubectl
mkdir -p ~/.local/bin
mv ./kubectl ~/.local/bin/kubectl

curl -LO https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
HELM_INSTALL_DIR=~/.local/bin bash ./get-helm-3 --no-sudo
rm ./get-helm-3
```