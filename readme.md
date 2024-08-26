# Persistent Volume Using Local Storage in Minikube

This repository demonstrates how to use local storage for persistent volumes in a Minikube Kubernetes cluster.

### Prerequisites
**Minikube**: Installed and running on your local machine.
**kubectl**: Installed and configured to interact with your Minikube cluster.

### Steps
1. Start Minikube
Ensure Minikube is running:

```bash
minikube start
```

2. Create a Storage Class
3. Create a Persistent Volume (PV)
4. Create a Persistent Volume Claim (PVC)
```bash
kubectl apply -f pv-local.yaml
```
5. Deploy a Pod to Copy Files

```bash
kubectl apply -f file-copy.yaml
```
6. Copy Files to the Pod, Use the following command to copy files from your local system to the pod:

```bash
kubectl cp <local-file-path> file-copy-pod:/data/
```

7. Deploy a Pod to Access Files
Deploy another pod to verify that you can access the files stored in the persistent volume:

```bash
kubectl apply -f file-access.yaml
```
8. Verify File Access
Exec into the pods to check if the files are accessible:

```bash
kubectl exec -it file-copy-pod -- sh
kubectl exec -it read-file-from-pvc -- sh
```