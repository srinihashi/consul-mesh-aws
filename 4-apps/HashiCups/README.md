# Deploying the HashiCups Microservives Application

## Create a Kubernetes namespace (hashicups)
```
$ kubectl create namespace hashicups
```

## Deploy the HashiCups Application in "hashicups" namespace
```
$ kubectl -n hashicups apply -f ./
```

## Test your deployment
### Retrieve your loadbalancer endpoint
```
$ kubectl -n hashicups get svc
```
### Use your web browser to connect to the endpoint


## Consul cluster peering
