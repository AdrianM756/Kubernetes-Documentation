## Application/Pod level logs
The ```/var/log``` directory in a Linux system is where you can find log files. These logs contain records of various system activities, events, and services

``` var/log/pods ``` Is where pods log files were stored.<br>

``` var/log/containers ``` Is where the container log files were stored.

**NOTE:** The files present in ```/var/log/containers``` are soft links to their respective ```/var/log/pods/<namespace_podname>``` folder.
<br>
<br>
## Crictl

```crictl``` Is a command-line interface for CRI-compatible container runtimes. it is use to inspect and debug container runtimes and applications on a Kubernetes node.

```crictl ps``` List all the containers.<br>

```crictl logs <container_name>``` Fetch the logs of the container.
<br>
<br>

## Journalctl

```journalctl``` Enables viewing and editing the systemd logs, making it a powerful tool for service and process debugging.

```journalctl -l -u kubelet``` To view logs of a kubelet service.
<br>

```journalctl -l -u kube-apiserver``` To view logs of a kube-apiserverservice.
<br>
<br>

## Kubernetes Events

Kubernetes ```events``` store information about the object state changes and errors. Events are stored in the API server on the control-plane node. 

```kubectl get events -n <namespace>``` Used in Kubernetes to retrieve events for a specific namespace.












