
# minikube-005
Build a Kubernetes Cluster Locally with Minikube. Deploy and manage apps in Kubernetes.

### Start Minikube (using Docker driver)
```
minikube start --driver=docker
```
![alt text](screenshots/minikubestart.png)
![alt text](screenshots/image-1.png)

###  Tools - Install kubectl and Minikube
```
kubectl version --client
```
Client Version: v1.31.0
Kustomize Version: v5.4.2

```
minikube version
```
minikube version: v1.37.0

### kubectl get nodes
```
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   8s    v1.34.0

```

### Deploy & Verify
1. Apply manifest
```
kubectl apply -f deployment.yaml
```
deployment.apps/my-nginx created

```
kubectl apply -f service.yaml
```
service/my-nginx-svc created

2. Resources

```
kubectl get deployments

```
![alt text](screenshots/deployments.png)

```
kubectl get pods -o wide
```
![alt text](screenshots/pods.png)

```
kubectl get svc
```
![alt text](screenshots/svc.png)

### Access the service
```
minikube service my-nginx-svc --url
```
http://192.168.49.2:31070

```
minikube tunnel
```
![alt text](screenshots/minikubetunnel.png)

### Logs
```
 kubectl logs my-nginx-5448d48675-qk887
 ```
![alt text](screenshots/logs.png)
![alt text](screenshots/logsc.png)

### 
```
kubectl describe pod my-nginx-5448d48675-qk887
```

![alt text](screenshots/despods.png)

![alt text](screenshots/despodss.png)

![alt text](screenshots/despodsss.png)

![alt text](screenshots/despodssss.png)

```
curl http://192.168.49.2:31070
```


![alt text](screenshots/htmlres.png)

### Scale and Update

### Scale replicas
```
kubectl scale deployment/my-nginx --replicas=3

kubectl get pods
```
![alt text](screenshots/scale.png)

![No of pods after increasing replicas](screenshots/noofpods.png)


### Rolling update
```
kubectl set image deployment/my-nginx nginx=nginx:1.26.0 --record

kubectl rollout status deployment/my-nginx
```
![alt text](screenshots/rollingupdate.png)

![Rolling Status](screenshots/rollingstatus.png)


### Namespace + ConfigMap

```
kubectl create namespace demo

kubectl create configmap demo-config --from-literal=GREETING="Hello from ConfigMap" -n demo

kubectl get configmap -n demo

```
![alt text](screenshots/namespace.png)
