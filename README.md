# KinD
## Create cluster

```sh
kind create cluster --config cluster.yaml --name local-tests
```

## Deploying Dashboard UI

#### Run this command:

```sh
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml
```

#### Create User

```sh
kubectl apply -f k8s-dashboard/clusterrolebinding.yaml -f k8s-dashboard/service-account.yaml
```

#### Getting Bearer Token
```sh
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
```

#### Proxy

```sh
kubectl proxy
```

Dashboard is available at http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/


## Deploy app-example

```sh
kubectl apply -f app-example
```

```sh
kubectl port-forward service/foo-service 5678
```

Application is available at localhost:5678