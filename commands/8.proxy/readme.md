

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
