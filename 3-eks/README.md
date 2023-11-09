# Connecting to your EKS Cluser
```
aws eks --region $(terraform output -raw cluster_region) update-kubeconfig --name $(terraform output -raw cluster_name)
```

## Test access to your EKS Cluster
```
kubectl get nodes
```
