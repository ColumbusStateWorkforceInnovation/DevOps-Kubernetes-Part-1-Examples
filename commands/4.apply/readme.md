
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
