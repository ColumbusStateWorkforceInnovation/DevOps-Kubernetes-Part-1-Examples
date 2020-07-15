# Pre Lab

Before starting the first lab you should install [Minikube][minikube]. Minikube is a tool that allows us to quickly spin up and run a single instance of Kubernetes locally.

To install it and the other tutorial dependencies, see the [Installation Guides](#installation-guide) section.

---

## Installation Guide

The steps below are from these install information links

* [minikube][install-minikube]
* [kubectl][install-kubectl]

## minikube 

download the binary

 ```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
```

make minikube executable
```
sudo mkdir -p /usr/local/bin/
sudo install minikube /usr/local/bin/
```

## kubectl

download 
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
```

make executable

```
sudo mv ./kubectl /usr/local/bin/kubectl
```

verify
```
kubectl version --client
```

should show output similar to:
```
Client Version: version.Info{Major:"1", Minor:"18", GitVersion:"v1.18.4", GitCommit:"c96aede7b5205121079932896c4ad89bb93260af", GitTreeState:"clean", BuildDate:"2020-06-17T11:41:22Z", GoVersion:"go1.13.9", Compiler:"gc", Platform:"linux/amd64"}
```


**Optionally** install [command completion][install-completion] for working with `kubectl`

Now time to [start and verify your Install](#start-and-verify).


---

## Start and Verify

With the software installed you can start your cluster using
```
minikube start --driver=docker
```

This will take a little bit of time the first time you run it

```
kubectl version
```

You should get output similar to the following:
```
Client Version: version.Info{Major:"1", Minor:"18", GitVersion:"v1.18.4", GitCommit:"c96aede7b5205121079932896c4ad89bb93260af", GitTreeState:"clean", BuildDate:"2020-06-17T11:41:22Z", GoVersion:"go1.13.9", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"18", GitVersion:"v1.18.3", GitCommit:"2e7996e3e2712684bc73f0dec0200d64eec7fe40", GitTreeState:"clean", BuildDate:"2020-05-20T12:43:34Z", GoVersion:"go1.13.9", Compiler:"gc", Platform:"linux/amd64"}

```

you may check status with
```
minikube status
```

now you may stop minikube with:
```
minikube stop
```

you can restart your minilube  with:
```
minikube start
```

and delete it with:
```
minikube delete
```


 [minikube]: https://github.com/kubernetes/minikube
 [install-kubectl]: https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl
 [install-minikube]: https://kubernetes.io/docs/tasks/tools/install-minikube/
 [install-completion]: https://kubernetes.io/docs/tasks/tools/install-kubectl/#enabling-shell-autocompletion