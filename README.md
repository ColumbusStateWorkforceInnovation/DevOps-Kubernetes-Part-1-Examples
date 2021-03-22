
# Infrastructure Automation Kubernetes Lab 1 

## Introduction: 

This lab is to help gain familiarity with the kubernetes client, `kubectl`.  It is the primary method of interacting with kubernetes and essential for using kubernetes. 

---
## Objective

For this lab, you will gain hands-on experience using kubectl and minikube. We will learn the basic commands used through the rest of the kubernetes course

---
## Getting Started:

1 - Copy the starter code from here into a new, private repository in your personal GitHub account. When adding a collaborator, be sure to add me ("cscc-luke-rouker").

---

## Understanding the Starter Code
This repository contains a basic manifest file in the manifests directory. We will be changing this then using `kubectl` commands to interact with it.

This respository also contains directories where we you will find examples of different commands. You will follow the readmes in these directories and save screenshots next to them to prove your work.

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


## Completing the Assignment



### 1 - Change manifest
Under manifests/basic-pod.yml change the the name of the pod from `basic-pod` to your first initial and last name. 

Example: if my name is John Doe the pod will be jdoe.

All places where `basic-pod` is used in this lab I want you to use your pod name.

--

### 2 - Go through examples
Under the commands directory you will see subfolders for some of the commands in kubectl.

 In each directory, there will be a readme with some info on the command and its use. You will follow each readme, run the commands under the examples section and and take a screenshot of your console.
 
 Save the file in each directory (one for each command you execute)

--

### 3 - More commands
Find *two* more commands not in the examples we went through from [kubetcl overview](https://kubernetes.io/docs/reference/kubectl/overview/) and execute them.

Take a screen shot of each command and save it in `additional` directory
 
 In addition, in the file `additional/additional_commands.txt` describe each of the two commands and what it is used for.

---


## Submitting Your Work

1- Publish your repository as a private repo, and ensure that you have pushed the latest version

2-  Submit the assignment in Blackboard with the link to your repo