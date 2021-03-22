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
