# k8s-tf-kind-cluster
Local K8S cluster on kind to test features &amp; resources

This cluster is hosted on Github Codespaces and created with KIND.
By default KIND does not have LoadBalancer Service. You may need to install cloud-provider-kind to enable LoadBalancer service.

## Instructions to download and Setup cloud-provider-kind on github codespace

### Prerequisites

***<ins>Make sure you have:</ins>***
* Docker
* Kind
* kubectl
* Go or download the prebuilt binary
```
docker --version
kind --version
kubectl version --client
```

1. Install using Go
``` 
go install sigs.k8s.io/cloud-provider-kind@latest 
```

2. Add the GO binary to your **PATH**
``` 
export PATH=$PATH:$(go env GOPATH)/bin 
```

3. Verify
``` 
cloud-provider-kind --help 
```

4. Install is completed

### Start the cloud-provider-kind
Start Cloud Provider KIND
``` 
cloud-provider-kind 
```

### Deploy an Application & expose it as load balancer
```
# create the deployment
kubectl create deployment nginx --image=nginx

# Create the Load Balancer Service
kubectl expose deployment nginx \
  --port=80 \
  --target-port=80 \
  --type=LoadBalancer
```

### Verify the loadbalancer IP:
**Before**
```
kubectl get svc

NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)
nginx        LoadBalancer   10.96.12.220    <pending>     80:30945/TCP
```

**After**
```
kubectl get svc

NAME         TYPE           CLUSTER-IP      EXTERNAL-IP    PORT(S)
nginx        LoadBalancer   10.96.12.220    172.18.0.5     80:30945/TCP
```