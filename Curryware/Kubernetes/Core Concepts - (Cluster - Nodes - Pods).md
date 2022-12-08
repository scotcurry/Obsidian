K8s is software for managing a **computer cluster**

**Nodes** are computers within a cluster.  It can be a physical or virtual computer within the cluster.

**Pods** are the executable units in a node.

To deploy NGINX in save the following in a file called nginx-deployment.yaml and run the command **kubectl apply -f nginx-deployment.yaml**

```
# nginx-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 1
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
        image: nginx:1.23.2
        ports:
        - containerPort: 80
```

In docker desktop you will see the instances show up.  To actually see them run

```
kubectl get pods
```

To run the bash shell in the container run (replace the info below with the info above):

```
kubectl exec -it nginx-deployment-66b6c48dd5-85nwq -- bash
```