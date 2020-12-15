# Kiali 

Installation of Kiali

## Installation 

```
istioctl manifest apply --set profile=demo
```

Check that kiali is installed:

```
kubectl -n istio-system get svc kiali
```

Otherwise run the following command:

```
istioctl manifest apply --set profile=demo --set values.kiali.enabled=true
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

