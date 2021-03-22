

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