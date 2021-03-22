
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
