# Kubernetes - Minikube

- Kubernetes: [https://kubernetes.io/](https://kubernetes.io/)
- Source: [https://github.com/thecyberbaby/Kubernetes](https://github.com/thecyberbaby/Kubernetes)

## Introduction

- minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

- All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away: minikube start

## What you’ll need

- 2 CPUs or more
- 2GB of free memory
- 20GB of free disk space
- Internet connection
- Container or virtual machine manager, such as: Docker, Hyperkit, Hyper-V, KVM, Parallels Podman, VirtualBox, or VMware

<p align="center">
    <img src="snaps/mikube.jpg" width="400" />
</p>

### Start  your cluster

From a terminal with administrator access (but not logged in as root), run:

	minikube start

### interacat with your cluster

If you already have kubectl installed, you can now use it to access your shiny new cluster:

	kubectl get po -A

Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

	minikube kubectl -- get po -A

## Manage your cluster

Pause Kubernetes without impacting deployed applications:

	minikube pause

Unpause a paused instance:

	minikube unpause

Halt cluster

	minikube stop

Increase the default memory limit (requires a restart):

	minikube config set memory 16384

Browse the catalog of easily installed Kubernetes services:

	minikube addons list

Create a second cluster running an older Kubernetes release:

	minikube start -p aged --kubernetes-version=v1.16.1

Delete all of the minikube clusters:

	minikube delete --all


## Basic controls

Start a cluster by running:

	minikube start

Access the Kubernetes dashboard running within the minikube cluster:

	minikube dashboard

Once started, you can interact with your cluster using kubectl, just like any other Kubernetes cluster. For instance, starting a server:

	kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4

Exposing a service as a NodePort

	kubectl expose deployment hello-minikube --type=NodePort --port=8080

minikube makes it easy to open this exposed endpoint in your browser:

	minikube service hello-minikube
Upgrade your cluster:

	minikube start --kubernetes-version=latest

Start a second local cluster (note: This will not work if minikube is using the bare-metal/none driver):

	minikube start -p cluster2

Stop your local cluster:

	minikube stop

Delete your local cluster:

	minikube delete

Delete all local clusters and profiles

	minikube delete --all

<p align="center">
    <img src="snaps/minikubeArchitecture.png" width="400" />
</p>

## In the end

Minikube is a `Kubernetes` SIGs project and has been started more than three years ago. It takes the approach of spawning a VM that is essentially a single node K8s cluster. Due to the support for a bunch of hypervisors it can be used on all of the major operating systems.
This also allows you to create multiple instances in parallel.

From a user perspective minikube is a very beginner friendly tool. You start the cluster using minikube start, wait a few minutes and your kubectl is ready to go. To specify a Kubernetes version you can use the `--kubernetes-version` flag. A list of supported versions can be found here.

If you are new to Kubernetes the first class support for its dashboard that minikube offers may help you. With a simple `minikube dashboard` the application will open up giving you a nice overview of everything that is going on in your cluster. This is being achieved by minikube’s addon system that helps you integrating things like, Helm, Nvidia GPUs and an image registry with your cluster.

