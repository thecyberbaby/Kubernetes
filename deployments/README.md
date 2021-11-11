# Deployments and ReplicaSet

A Deployment provides declarative updates for `Pods` and `ReplicaSets`.

You describe a desired state in a Deployment, and the Deployment `Controller` changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.

Note: Do not manage ReplicaSets owned by a Deployment. Consider opening an issue in the main Kubernetes repository if your use case is not covered below.

## Creating a Deployment 

The following is an example of a Deployment. It creates a ReplicaSet to bring up three nginx Pods:

	apiVersion: apps/v1
	kind: Deployment
	metadata:
	  name: nginx-deployment
	  labels:
	    app: nginx
	spec:
	  replicas: 3
	  selector:
	    matchLabels:
	      app: nginx
	  template:
	    metadata:
	      labels:
	        app: nginx
	    spec:
	      containers:
	      - name: nginx
	        image: nginx:1.14.2
	        ports:
	        - containerPort: 80
