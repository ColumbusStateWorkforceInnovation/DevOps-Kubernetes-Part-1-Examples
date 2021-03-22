# Infrastructure Automation Kubernetes Pre-lab

## Introduction: 

In this lab, you will install and start to use Minikube - a which acts like a local Kubernetes.  

## Objective

For this lab, you will install the required tools needed to continue with the kubernetes course.



## Instructions:


The steps below are from these install information links

* [minikube][install-minikube]
* [kubectl][install-kubectl]
---
## install minikube 

1- download the binary

 ```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
```

2- make minikube executable
```
sudo mkdir -p /usr/local/bin/
sudo install minikube /usr/local/bin/
```

## install kubectl
---
1- download
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
```

2- make executable

```
sudo mv ./kubectl /usr/local/bin/kubectl
```
3- verify
```
kubectl version --client
```

4- Validate output - should be

output should be similar to:
```
Client Version: version.Info{Major:"1", Minor:"18", GitVersion:"v1.18.4", GitCommit:"c96aede7b5205121079932896c4ad89bb93260af", GitTreeState:"clean", BuildDate:"2020-06-17T11:41:22Z", GoVersion:"go1.13.9", Compiler:"gc", Platform:"linux/amd64"}
```

**Optionally** install [command completion][install-completion] for working with `kubectl`

---

## verify minikube installation


1- run the following to get the status

```
minikube status
```

2- run the following to stop minikube
```
minikube stop
```

3- run the following restart your minikube:
```
minikube start
```

4-  finally delete the minikube instance with:
```
minikube delete
```




## Submitting Your Work

Nothing to submit

[minikube]: https://github.com/kubernetes/minikube
[install-kubectl]: https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl
[install-minikube]: https://kubernetes.io/docs/tasks/tools/install-minikube/
[install-completion]: https://kubernetes.io/docs/tasks/tools/install-kubectl/#enabling-shell-autocompletion
