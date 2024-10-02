# Kubernetes


## kubectl

[Official K8s Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

```bash
alias k=kubectl


# bash in pod
k exec -it <pod-name> — /bin/bash

k get all  # list all resources

k get services  # List all services in the namespace
k get pods —all-namespaces  # List all pods in all namespaces
k get pods -o wide  # List all pods in the namespace, with more details
k get deployment my-dep  # List a particular deployment

k describe nodes <node-name>
k describe pods <pod-name>

k delete -f ./pod.yaml  # Delete a pod using the type and name specified in pod.yaml
k delete pod,service baz foo  # Delete pods and services with same names “baz” and “foo”
k delete pods,services -l name=<Label>  # Delete pods and services with label name=myLabel
k -n <namespace> delete po,svc —all  # Delete all pods and services in namespace my-ns


# Port Forwarding
k port-forward deployments/labelname 8080:8080  # deployment
k port-forward svc/labelname 8080:8080  # service


# Explain
k explain pod.spec

# Editing
k edit deployments/name

# Controller Status
> k get cs
NAME                 STATUS    MESSAGE             ERROR
scheduler            Healthy   ok
controller-manager   Healthy   ok
etcd-0               Healthy   {"health":"true"}
```

## Best Practices

- https://learnk8s.io/production-best-practices


## Troubleshooting

- https://learnk8s.io/troubleshooting-deployments


## API Gateway

- https://learnk8s.io/kubernetes-ingress-api-gateway
- https://www.nginx.com/blog/microservices-march-protect-kubernetes-apis-with-rate-limiting/



## Learning

- https://learnk8s.io/archive