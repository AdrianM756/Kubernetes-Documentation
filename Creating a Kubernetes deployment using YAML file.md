## Creating a Kubernetes deployment using a YAML file

**YAML(YAML Ain’t Markup Language)** is one of the well-known language that is use for a configuration file. It's in human-readable format making it easy to understand or modify to configuration content.

Using YAML in a kubernetes deployment allows to create, update, or delete Deployments in a Kubernetes cluster. the YAML file contains a set of key-value pairs that specify various attributes and parameters for the Deployment, such as the number of replicas, pod template specifications, labels, and more.

On this documentation, we will use an image of ```nginx:alpine``` for our deployment. Make sure that docker is already installed on the system.

For the Kubernetes deployment YAML file, we will be using this configuration to create a container using the image ```nginx:alpine``` with 4 replicas. we will then name this file as  ```nginx-alpine-deployment.yaml```.

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

To use the YAML file the we've created, we will use the command:

```
kubectl apply -f nginx-alpine-deployment.yaml
```
**NOTE:** Don't forget to use the ``-f`` parameter as it represents the file that will be used.

To check if the creation succeed, you can use the command ```kubectl get deployment``` and you should be able to see similar output.

![image](https://github.com/user-attachments/assets/b3ba3189-fe4c-4133-901c-5cff3ad0714e)



## Author:
- [Sef Adrian Milambiling](https://github.com/AdrianM756)
