# Creating and managing pods

At the core of Kubernetes is the pod. pods represent a logical application and hold a collection of one or more containers and volumes. In this lab you will learn how to:

* Write a pod configuration file
* Create and inspect pods 
* Interact with pods remotely using kubectl

In this lab you will create a pod named `monolith` and interact with it using the kubectl command line tool.

## Tutorial: Creating pods

Explore the `monolith` pod configuration file:

```
cat pods/monolith.yaml
```

Create the `monolith` pod using kubectl:

```
kubectl create -f pods/monolith.yaml
```

## Exercise: View pod details

Use the `kubectl get` and `kubectl describe` commands to view details for the `monolith` pod:

### Hints

```
kubectl get pods
```

```
kubectl describe pods <pod-name>
```

### Quiz

* What is the IP address of the `monolith` pod?
* What node is the `monolith` pod running on?
* What containers are running in the `monolith` pod?
* What are the labels attached to the `monolith` pod?
* What arguments are set on the `monolith` container?

## Exercise: Interact with a pod remotely

pods are allocated a private IP address by default and cannot be reached outside of the cluster. Use the `kubectl port-forward` command to map a local port to a port inside the `monolith` pod. 

### Hints

Use two terminals. One to run the `kubectl port-forward` command, and the other to issue `curl` commands.

```
kubectl port-forward monolith 10080:8080
```

```
curl http://127.0.0.1:10080
```

```
curl http://127.0.0.1:10080/secure
```

```
curl -u user http://127.0.0.1:10080/login
```

> Type "password" at the prompt.

```
curl -H "Authorization: Bearer <token>" http://127.0.0.1:10080/secure
```

> Use the JWT token from the previous login.

## Exercise: View the logs of a pod

Use the `kubectl logs` command to view the logs for the `monolith` pod:

```
kubectl logs monolith
```

> Use the -f flag and observe what happens.

## Exercise: Get an interactive shell inside a pod



Use the `kubectl exec --stdin --tty <pod>  -- /bin/sh` command to get a shell inside the `monolith` pod
