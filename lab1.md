# Intro to kubectcl

This lab is to help gain familiarity with the kubernetes client, `kubectl`.  It is the primary method of interacting with kubernetes and essential for using kubernetes. 

## For this lab do the following -

## **Step 1** - 

create a directory on your vm somewhere called `manifests`. Inside this directory create a manifest file called `basic-pod.yaml`

inside the yaml add the following configuration:

```
apiVersion: v1
kind: Pod
metadata:
  name: basic-pod
spec:
  containers:
  - name: nginx
    image: nginx:stable-alpine
    ports:
    - containerPort: 80
```

Change the the name of the pod from `basic-pod` to your first initial and last name. Example if my name is John Doe the pod will be jdoe.

All places wehre `basic-pod` is used in this lab I want you to use your pod name

## **Step 2** -

 For *each* command described below I would like you follow the example for each command and take screenshot of the terminal. Save the picture with the format <command_name>_number. 

So for the `kubectl create` example - the file name would be `create_1.ext` where ext is whatever format your computer saves it as. If there are multiple commands save them sequentially `create_2.ext` and `create_3.ext`  ect..

## **Step 3** -

 Find *two* more commands not in the examples from [kubetcl overview](https://kubernetes.io/docs/reference/kubectl/overview/) and execute them and also take screenshots for each new command and saving the files as we did in step 2.
 
 In addition in a text file, describe each of the two commands and what it is used for. Save this file as `additional_commands.txt`



## **Step 4** -

Zip all your **screenshots**, your **additional_commands.txt** and your **manifest** and upload to blackboard as `firstname_lastname_lab_1.zip`



<br>

- - -

# Commands

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

## Basic Commands
The most used `kubectl` commands you should know are `get`, `create`,
`apply`, `delete`, `describe`, and `logs`.  

Help with commands can be gotten via `kubectl --help` or for a specific command `kubectl <command> --help`


---


### `kubectl create`
`kubectl create` creates an object from the cli or with a path to a manifest using the `-f` or  `--filename` flag that can point to either a manifest file, or a directory that has multiple

**Command**
```
kubectl create <TYPE> <args>
kubectl create -f <path>
```

**Examples**
```
$ kubectl create namespace dev
namespace/dev created

kubectl create -f manifests/basic-pod.yaml 
pod/basic-pod created
```


### `kubectl get`
`kubectl get` Lists one or more objects of a certain type.

**Command**
```
kubectl get <TYPE>
kubectl get <TYPE> <NAME>
kubectl get <TYPE> <NAME> <args>
```

**Examples**
```
$ kubectl get namespaces
NAME              STATUS   AGE
default           Active   132m
dev               Active   118s
kube-node-lease   Active   132m
kube-public       Active   132m
kube-system       Active   132m

$ kubectl get pods
NAME        READY   STATUS    RESTARTS   AGE
basic-pod   1/1     Running   0          87s

$ kubectl get pod basic-pod
NAME        READY   STATUS    RESTARTS   AGE
basic-pod   1/1     Running   0          107s

$ kubectl get pod basic-pod -o wide
NAME        READY   STATUS    RESTARTS   AGE    IP           NODE       NOMINATED NODE   READINESS GATES
basic-pod   1/1     Running   0          2m4s   172.18.0.4   minikube   <none>           <none>

```

---

### `kubectl delete`
`kubectl delete` this command deletes the object.

**Command**
```
kubectl delete <TYPE> <NAME>
```

**Examples**
```
$ kubectl delete pod basic-pod
pod "basic-pod" deleted
```

---

### `kubectl apply`

`kubectl apply` is like `kubectl create`. It will create the resource if it does not exist of update the resource if it is already created.

It is similar to `kubectl create` and takes a `-f` path to the manifest or reads in the config from the cli's stdin.

**Command**
```
kubectl apply -f <path>
```

**Notes**

When objects are created in kubernetes we learned that its state/config is stored within kubernetes. When you update a resource, it will store the previous version of it in an `annotation`.

`kubectl apply` behavior ff the object was not created initially with `apply` will act as a diff between the two. If you use apply on an object created via `create` you will get warning.

```
kubectl apply -f manifests/basic-pod.yaml 
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
pod/basic-pod configured
```

[kubectl apply documentation](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/#kubectl-apply)


**Examples**
```
$ kubectl apply -f manifests/basic-pod.yaml 
pod/basic-pod created
```

---

### `kubectl edit`
`kubectl edit` allows for in place modification with your text editor without having to apply. 

This command is useful for debugging, and **should not** be used in production since changes made are not tracked like `apply`.

**Command**
```
$ kubectl edit <TYPE> <NAME>
```

**Examples**
```
$ kubectl edit pod basic-pod

# Please edit the object below. Lines beginning with a '#' will be ignored,
# and an empty file will abort the edit. If an error occurs while saving this file will be
# reopened with the relevant failures.
#
apiVersion: v1
kind: Pod
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","kind":"Pod","metadata":{"annotations":{},"name":"basic-pod","namespace":"default"},"spec":{"containers":[{"image":"nginx:stable-alpine","name":"nginx","ports":[{"containerPort":80}]}]}}
  creationTimestamp: "2020-07-15T02:20:28Z"
  managedFields:
  - apiVersion: v1
    fieldsType: FieldsV1
    fieldsV1:
      f:metadata:
        f:annotations:
          .: {}
          f:kubectl.kubernetes.io/last-applied-configuration: {}
      f:spec:
        f:containers:
          k:{"name":"nginx"}:
            .: {}
            f:image: {}
            f:imagePullPolicy: {}
            f:name: {}
            f:ports:
              .: {}
              k:{"containerPort":80,"protocol":"TCP"}:
                .: {}
                f:containerPort: {}
                f:protocol: {}
            f:resources: {}
            f:terminationMessagePath: {}
            f:terminationMessagePolicy: {}
        f:dnsPolicy: {}
        f:enableServiceLinks: {}
        f:restartPolicy: {}
        f:schedulerName: {}
        f:securityContext: {}
        f:terminationGracePeriodSeconds: {}
    manager: kubectl
    operation: Update
    time: "2020-07-15T02:20:28Z"
  - apiVersion: v1
    fieldsType: FieldsV1
    fieldsV1:
      f:status:
   
   .... omitted for brevity
```


---

### `kubectl describe`
`kubectl describe` lists information about the specific object.
**Command**
```
kubectl describe <TYPE>
kubectl describe <TYPE> <NAME>
```

**Examples**
```
$ kubectl describe pod basic-pod
Name:         basic-pod
Namespace:    default
Priority:     0
Node:         minikube/172.17.0.3
Start Time:   Tue, 14 Jul 2020 22:20:28 -0400
Labels:       <none>
Annotations:  Status:  Running
IP:           172.18.0.4
IPs:
  IP:  172.18.0.4
Containers:
  nginx:
    Container ID:   docker://7fb050f8ec78d7fe3994472b2f385c05b3dece96be6771b90c69592dedff6a90
    Image:          nginx:stable-alpine
    Image ID:       docker-pullable://nginx@sha256:29dc24ed982665eb88598e0129e4ec88c2049fafc63125a4a640dd67529dc6d4
    Port:           80/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Tue, 14 Jul 2020 22:20:29 -0400
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-hj99j (ro)
Conditions:
  Type              Status
  Initialized       True 
  Ready             True 
  ContainersReady   True 
  PodScheduled      True 
Volumes:
  default-token-hj99j:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-hj99j
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  7m32s  default-scheduler  Successfully assigned default/basic-pod to minikube
  Normal  Pulled     7m31s  kubelet, minikube  Container image "nginx:stable-alpine" already present on machine
  Normal  Created    7m31s  kubelet, minikube  Created container nginx
  Normal  Started    7m31s  kubelet, minikube  Started container nginx

  ```

---

### `kubectl logs`
`kubectl logs` outputs `stdout` and `stderr` logs from a pod. If more than one container exists use the `-c` flag with the container name.

**Command**
```
kubectl logs <NAME>
kubectl logs <NAME> -c <container-name>
```

**Examples**
```
$ kubectl logs basic-pod
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up

```

---


### `kubectl proxy`
`kubectl proxy` lets us run a proxy to the Kubernetes API server. Using `-p` or `--port` we can specify where to proxy to.

**Command**
```
kubectl proxy
kubectl proxy --port=<PORT>
```

**Examples**
```
$ kubectl proxy
Starting to serve on 127.0.0.1:8001

```

then open another tab
```
$ curl 127.0.0.1:8001/version
{
  "major": "1",
  "minor": "18",
  "gitVersion": "v1.18.3",
  "gitCommit": "2e7996e3e2712684bc73f0dec0200d64eec7fe40",
  "gitTreeState": "clean",
  "buildDate": "2020-05-20T12:43:34Z",
  "goVersion": "go1.13.9",
  "compiler": "gc",
  "platform": "linux/amd64"


```

**Notes**

The proxy follows the pattern:
```
http://<proxy_address>/api/v1/namespaces/<namespace>/<object>/<name>[:port_name]/proxy
```
So for the basic-pod we can curl it directly

**Examples**
```
$ curl http://127.0.0.1:8001/api/v1/namespaces/default/pods/basic-pod/proxy/

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

```
OR you can visit the url in your browser and you should see the nginx-homepage

In the pre-lab we used `minikube dashboard` to open the dashboard page. Similarly after using `kubectl proxy` we can visit the dashboard by visiting 

http://127.0.0.1:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
