# Istio 

Download and installation of Istio

## Download 

```
# Download
curl -L https://istio.io/downloadIstio | sh -

# Move to the Istio package directory
cd istio-1.8.1

# Add the istioctl client to your path
export PATH=$PWD/bin:$PATH
```

## Installation on master node

```
# For this installation, we use the demo configuration profile. 
istioctl install --set profile=demo -y

# Add a namespace label to instruct Istio to automatically inject Envoy sidecar proxies when you deploy your application later
kubectl label namespace default istio-injection=enabled
```

Deploy your applications
