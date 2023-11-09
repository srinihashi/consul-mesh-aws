# Set up federation between the EKS and AKS clusters

## Step-1: Enable federation / peering through Consul mesh on each cluster
### On EKS
```
$ kubectl -n consul apply -f enable-mesh-peering.yaml
```

### On AKS
```
$ kubectl -n consul apply -f enable-mesh-peering.yaml
```

## Step-2: Peering
### On EKS:
using Consul UI goto "peering" --> "Add peer connection" --> "Generate token", and generate token, and copy the token
### On AKS:
using Consul UI goto "peering" --> "Add peer connection" --> "Establish peering", and past the token, and "Add peer"

## Step-3: Export the necessary services in AKS - (shippingservice)
### On AKS:
apply the "export-services.yaml" file

```
$ kubectl -n google apply -f 
```

## Step-4: Create Servive Rresolver to failover to exported services (running in AKS) 
### On EKS:
apply the "service-resover.yaml" file

```
$ kubectl -n goolge apply -f service-resolver.yaml
```
