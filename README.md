
# Infrastructure Automation Kubernetes Week 1 Examples

## Introduction: 

This repo is to help gain familiarity with the kubernetes client, `kubectl`.  It is the primary method of interacting with kubernetes and essential for using kubernetes. 

---
## Objective

With these examples, you will gain hands-on experience using kubectl and minikube. We will learn the basic commands used through the rest of the kubernetes course

---
## Getting Started:

MAKE SURE TO HAVE GONE THROUGH THE ENV_SETUP.md and followed the instructions there.

---

## Understanding the Starter Code
This repository contains a basic manifest file in the manifests directory. We will be changing this then using `kubectl` commands to interact with it.

This respository also contains directories where we you will find examples of different commands. 

---

## What are commands?

`kubectl` commands follow the following syntax

```
kubectl [command] [TYPE] [NAME] [flags]
```

* **command** - The command to perform -  `get`, `create`, `apply` and `delete`.
* **TYPE** - The resource or object - like `pods` or `service`
* **NAME** - Specifies the name of the resource. Names are case-sensitive. If the name is omitted, details for all resources are displayed.
* **flags** - Optional arguments to pass to the command - like `--all-namespaces`

**Examples**
```
$ kubectl create -f basic-pod.yaml
$ kubectl get pods --all-namespaces 
$ kubectl delete pod basic-pod
$ kubectl describe pod basic-pod
```

---

### 1 - Change manifest
Under manifests/basic-pod.yml change the the name of the pod from `basic-pod` to your first initial and last name. 

All places where `basic-pod` is used in these examples, use your pod name.

--

### 2 - Go through examples
Under the commands directory you will see subfolders for some of the commands in kubectl.

 In each directory, there will be a readme with some info on the command and its use. You will follow each readme and run the commands under the examples section

--

### 3 - More commands
Find *two* more commands not in the examples we went through from [kubetcl overview](https://kubernetes.io/docs/reference/kubectl/overview/) and execute them.

