# Kiali 

Installation of Kiali

## Installation 

```
kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.7/samples/addons/kiali.yaml
```

## Configuration

```
# Check kiali service
kubectl -n istio-system get svc kiali

# If ec2 aws - Edit kiali service
kubectl -n istio-system edit svc kiali

# Change of ClusterIp to NodePort

Access your ip with kiali port

# If local cluster
istioctl dashboard kiali
```
Default credentials
- User: admin
- Password: admin 

