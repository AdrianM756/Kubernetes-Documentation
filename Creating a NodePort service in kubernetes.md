## Creating a NodePort service in kubernetes

[NodePort](https://kubernetes.io/docs/concepts/services-networking/service/) Exposes the Service on each Node's IP at a static port. It serves as the external entry point for incoming requests for your pod. Keep in mind that the NodePort service is not recommended for high-traffic applications, as they do not provide load balancing or failover capabilities out of the box.
## Setting up NodePort Service

On this demo, we will first create a YAML file to deploy multipe pods. We will name this as ```nginx-alpine-deployment.yaml``` below are the YAML config:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-alpine-deployment
spec:
  replicas: 4
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx-container
        image: nginx:alpine
        ports:
        - containerPort: 80
```
We will then run this YAML file that we've created for our deployment using the command:

```
kubectl apply -f nginx-alpine-deployment.yaml
```

Next, we will be creating the YAML configuration file for our NodePort service and expose it to port ```32000```.  We will then simply name this as ```Nodeport.yaml``` for this demo.

```
apiVersion: v1
kind: Service
metadata:
  name: nginx-nodeport
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      nodePort: 32000
```

**NOTE:** The port range of NodePort is within ```30000-32767```

We will then run this YAML file that we've created for our NodePort using the command:

```
kubectl apply -f nodeport.yaml
```

to verify that our NodePort is running, we can use the command:

```
kubectl get service nginx-nodeport 
```

You should be able to get a similar output:

```
  NAME             TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
nginx-nodeport   NodePort     <IP ADDRESS>    <none>        80:32000/TCP   25m
```

**NOTE:** Keep in mind that ```CLUSTER-IP``` is not the originally IP address set as it should be a Public IP address. but for this demo, we will be not showing the actual IP address.

Using our browser we should now be able to access our nginx using:

```
http://<CLUSTER-IP>:32000
```

We should be getting this output:

![image](https://github.com/user-attachments/assets/5c3d32b1-068d-4e23-a170-655713f860a4)

## Author:
[Sef Adrian Milambiling](https://github.com/AdrianM756)


