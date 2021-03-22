
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
