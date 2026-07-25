# k8s-tf-kind-cluster
Local K8S cluster on kind to test features &amp; resources

This cluster is hosted on Github Codespaces and created with KIND.
By default KIND does not have LoadBalancer Service. You may need to install cloud-provider-kind to enable LoadBalancer service.

## Follow below Instructions to download and Setup cloud-provider-kind on github codespace

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
`go install sigs.k8s.io/cloud-provider-kind@latest`
