# Kubernetes Manifests for Jenkins Deployment

Refer https://devopscube.com/setup-jenkins-on-kubernetes-cluster/ for step by step process to use these manifests.


## Experiment in
- kubernetes in docker-desktop (macOS)
- local volume



1. Create Jenkins with k8s
```
kubectl create -f namespace.yaml

kubectl apply -f serviceAccount.yaml

kubectl create -f volume.yaml

kubectl apply -f deployment.yaml

kubectl apply -f service.yaml

```

2. Go to jenkins admin
```
kubectl get services -n jenkins-batch
NAME              TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
jenkins-service   NodePort   10.98.161.215   <none>        8080:32000/TCP   95s
```

http://localhost:32000/
![](https://www.jenkins.io/doc/book/resources/tutorials/setup-jenkins-01-unlock-jenkins-page.jpg)


```
# Get the initial password from pod log
kubectl get pods -n jenkins-batch
NAME                       READY   STATUS    RESTARTS   AGE
jenkins-5498fbb866-4b5m8   1/1     Running   0          9m21s

kubectl logs jenkins-5498fbb866-4b5m8 -n jenkins-batch
```
