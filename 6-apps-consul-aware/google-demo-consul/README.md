# Deploy Google demo app to AKS

## Step-1: Create a new namescpace (google)
```
kubectl create namespace google
```
## Step-2: deploy google app
```
kubectl -n google apply -f ./
```
