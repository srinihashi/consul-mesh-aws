# Set up federation between the EKS and AKS clusters

## Step-1: Deploy the Mesh Gateway on both clusters
### on EKS
```
helm -n consul upgrade consul hashicorp/consul --version "1.2.0" --values values.yaml
```

### on AKS
```
helm -n consul upgrade consul hashicorp/consul --version "1.2.0" --values values.yaml
```

## Step-2: Enable federation / peering through Consul mesh on each cluster
### On EKS
```
kubectl -n consul apply -f enable-mesh-peering.yaml
```

### On AKS
```
$ kubectl -n consul apply -f enable-mesh-peering.yaml
```

## Step-3: Peering
### On EKS:
using Consul UI goto "peering" --> "Add peer connection" --> "Generate token", and generate token, and copy the token
### On AKS:
using Consul UI goto "peering" --> "Add peer connection" --> "Establish peering", and past the token, and "Add peer"

## Step-4: Export the necessary services in AKS - (shippingservice)
### On AKS:
```
$ kubectl -n google apply -f export-services.yaml
```

## Step-: Create Servive Rresolver to failover to exported services (running in AKS) 
### On EKS:
```
$ kubectl -n goolge apply -f service-resolver.yaml
```
