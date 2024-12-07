# Kubernetes Notes

## Table of Contents
1. [Introduction](#introduction)
2. [Basic Concept](#basic-concept)
3. [Architecture](#architecture)
4. [Components](#components)
5. [Setup and Installation](#setup-and-installation)
6. [Basic Commands](#basic-commands)
7. [Advanced Topics](#advanced-topics)
8. [Troubleshooting](#troubleshooting)
9. [Resources](#resources)

## Introduction
### 網站教學
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Kubernetes 教學](https://kubernetes.io/docs/tutorials/)

## Basic Concept
### Kubernetes Cluster
[官網文件](https://kubernetes.io/docs/tutorials/kubernetes-basics/create-cluster/cluster-intro/)
- Kubernetes 使 deploy containerized applications 更容易，以前要一個個 container 安裝到各自的 machine 上面， k8s 使我們可以一次管理 cluster of pods。
  > **Kubernetes automates the distribution and scheduling of application containers across a cluster in a more efficient way.
- Kubernetes 由兩個部分組成
  > Control Planes manage the cluster and the nodes that are used to host the running applications.
  1. **Control Plane** 負責 coordinates cluster
  2. **Nodes** 是 worker, 執行 applications
    - 可能是 VM 或是 pysical computer
    - **Kubelet**
      - 每個 node 都有
      - 負責管理 node, 並負責跟 control plain 溝通

  ![Cluster Diagram](images/k8s-cluster.png)
- 我們使用 [Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/) 來與 control plain 做互動

### Deployment
當我們有正在 running 的 cluster, 我們就可以使用 **Deployment** deploy containerized application.
當我們 create **Deployment** 之後, Kubernetes 的 control plain 會控制執行這些 application 的 nodes. 提供 **self-healing mechanism**, 恢復 failure 的 nodes
![Deployment](images/deployment.jpg)
### Pods and Nodes
- Pods
  - Pods host 我們給他們的 application
  - Pods 共享些資源
    - Shared storage, as **Volumes**
    - Networking, as a **unique cluster IP address**
    - Information about how to run each container, such as the container image version or specific ports to use
  - **Pod**
    - 一個 **Pod** 可以包含一個或多個 container, 例如 Node.js app + Node.js webserver
    - 同個 pod 內的 container 共享同個 IP address 跟 port space
    - 一個 pod 是 **atomic unit**, 最小單位，不可再分割

## Architecture
// ...existing code...

## Components
// ...existing code...

## Setup and Installation
// ...existing code...

## Basic Commands
### 建立 cluster
```bash
minikube start
```
### create deployment
```bash
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
```
### deploy docker image
```bash
kubectl create deployment hello-minikube1 --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube1 --type=LoadBalancer --port=8080
```

### 查看 Pod 狀態
#### 所有 pod 
```bash
kubectl get pods
```
範例
 ```sql
 NAME                            READY   STATUS    RESTARTS   AGE
hello-minikube-5c7d68d46c-jzlp2 1/1     Running   0          5m
nginx-deployment-758c6c6df9-qpx2q   1/1     Running   0          10m
```
- NAME： Pod 的名稱。
- READY： 已就緒的容器數量（1/1 表示 1 個容器已就緒）。
- STATUS： Pod 的目前狀態（如 Running, Pending, Completed）。
- RESTARTS： 容器的重啟次數。
- AGE： Pod 運行的時間。
#### 查看 Namespace 的 pods
```bash
kubectl get pods -n <namespace>
```
#### 顯示更多資料
```bash
kubectl get pods -o wide
```
#### 輸出 pod 的 yaml file 內容
```bash
kubectl get pods <pod-name> -o yaml
```
### 查看 node port
```bash
kubectl get svc 
```
範例
```sql
NAME             TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
hello-minikube   NodePort    10.98.207.67   <none>        8080:32033/TCP   29m
kubernetes       ClusterIP   10.96.0.1      <none>        443/TCP          37m
```
### 看 pod 的 log
```bash
kubectl logs <pod-name>
```
### Expose the Pod 到 public internet, 使用 the kubectl expose command:
```bash
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```
### 刪除
```
kubectl delete service hello-node
kubectl delete deployment hello-node
```
### 停止
```bash
minikube stop
```



## Advanced Topics
// ...existing code...

## Troubleshooting
// ...existing code...

## Resources
// ...existing code...