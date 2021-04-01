# Ingress NGINX

### Create cluster

```sh
kind create cluster --config cluster.yaml --name local-tests
```

### Run this command

```sh
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/kind/deploy.yaml
```

### Deploy app-example.yaml

```sh
kubectl apply -f app-example.yaml
```
Applications are available at localhost/foo and localhost/bar