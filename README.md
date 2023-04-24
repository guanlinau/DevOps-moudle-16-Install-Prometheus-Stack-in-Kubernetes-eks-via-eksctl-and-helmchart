### Project name:

Install Prometheus Stack in Kubernetes to monitor Microservices

### Technologies used:

Prometheus, Kubernetes, Helm, AWS EKS, eksctl, Grafana, Linux

### Project Description:

1- Setup EKS cluster using eksctl

2- Deploy microservices to k8s cluster

3- Deploy Prometheus, Alert Manager and Grafana in cluster as part of the Prometheus Operator using Helm chart

### Instruction

###### Step 1: Create eksctl in default region

```
aws configure
```

```
eksctl create cluster -name my-cluster
```

# eksctl will configure the credentials with eks cluster for kubectl and save it to kubeconfig

![image](images/Screenshot%202023-04-25%20at%209.16.33%20am.png)
![image](images/Screenshot%202023-04-25%20at%209.21.19%20am.png)

###### Step 2: Deploy microservices to my-cluster

```
kubectl apply -f config-microservices.yaml
```

![image](images/Screenshot%202023-04-25%20at%209.19.21%20am.png)

###### Step 3: Deploy prometheus, alert manager and Grafana via helm chart

#Add repo

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

#Update the repo chart

```
helm repo update
```

#Create a new namespace for prometheus

```
kubectl create namespace monitoring
```

#Deploy prometheus via helm chart

```
helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring
```

![image](images/Screenshot%202023-04-25%20at%209.27.39%20am.png)
