Deployments are an object in Kubernetes used to describe the desired state of subset of pods in a cluster. Once a Deployment is created, various controllers in the cluster use it to create other API objects, and eventually have the desired number
of pods running in a cluster.

## Create a deployment

On this documentation, we will use an image of **nginx:alpine** for our deployment. Make sure that docker is already installed on the system. if the image **nginx:alpine** is not on the system yet, you can use the following command:

```
  docker pull nginx:alpine
```
You should be able to get a similar output

![image](https://github.com/user-attachments/assets/cddf17f1-9bfe-40f9-8283-d161bab7be4e)

To verift that it us already installed, you ca use the command:

```
docker images
```
![image](https://github.com/user-attachments/assets/288969e1-d7ba-4f0b-8b84-29c857bbe6d2)

To Create the deployment use the following commands:

```
kubectl create deployment <NAME OF YOUR DEPLOYMENT> --image=nginx:alpine
```
To verify the deployment status, use the command:

```
kubectl get deployment <NAME OF YOUR DEPLOYMENT>
```

## Scaling a deployment

Deployments provide an easy way to scale up an application by running more pods.

On this system, we will try to replicate 3 of the deployment that we've just created. To do this, we will use the command:

```
kubectl scale deployment/<NAME OF THE DEPLOYMENT> --replicas=3
```
The ``` --replica=3``` is the parameter that we use to specify the number of deployments that we want to replicate.

**NOTE:** Keep in mind that there are are other Kubernetes resources that offer the same scaling mechanisms, it's important to make sure we're scaling a **deployment**.

To the verify if all the replicas are running, use the command:

```
kubectl get deployment <NAME OF YOUR DEPLOYMENT>
```
You should be able to get a similar output. As you will notice that the 3 replication that we've just created are now available and running.

![image](https://github.com/user-attachments/assets/dc8b70c0-1b36-40a0-bfb4-6fe6cb75cf0f)

## Scaling down a deployment 

Like scaling a deployment, it can also be scaled down. For this instance, we will scale it down to 2 replicas. to do this, use the command:

```
kubectl scale deployment/<NAME OF THE DEPLOYMENT> --replicas=2
```
To verify that it takes effect, we can use the command:

```
kubectl get deployment <NAME OF YOUR DEPLOYMENT>
```
You should be able to get a similar output. As you will notice, the number of available and running deployment are just 2.

![image](https://github.com/user-attachments/assets/bc9e70fa-d862-402b-b839-3821a519df30)











## References:
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#scaling-a-deployment

