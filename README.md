

# WordPress on Kubernetes with MySQL and phpMyAdmin

This project demonstrates how to deploy **WordPress** with a **MySQL database** and **phpMyAdmin** on a Kubernetes cluster using YAML manifests.

## 🛠️ Prerequisites

* A running Kubernetes cluster (Minikube, Kind, or Cloud-based cluster)
* `kubectl` CLI installed and configured
* Persistent storage configured (for PV/PVC)

---

## 🚀 Deployment Steps

### 1. Create a Namespace

```bash
kubectl create -f ns.yaml
kubectl get all -n wordpress
```

### 2. Create Secrets for MySQL Database

```bash
kubectl create -f secret.yaml
kubectl describe secret/db-secret -n wordpress
```

### 3. Create Persistent Volumes (PV) and Persistent Volume Claims (PVC)

For database:

```bash
kubectl create -f pvpvc.yaml
```

For WordPress:

```bash
kubectl create -f pvpvcwp.yaml
```

### 4. Deploy MySQL Database

```bash
kubectl create -f dbdepsvc.yaml
kubectl get svc -n wordpress
kubectl get ep -n wordpress
kubectl get po -n wordpress
```

### 5. Deploy phpMyAdmin

```bash
kubectl create -f phpdepsvc.yaml
kubectl get svc -n wordpress
```

### 6. Deploy WordPress

```bash
kubectl create -f wordpressdepsvc.yaml
kubectl get all -n wordpress
```

---

## ✅ Verification

* Once all pods and services are running, you will have:

  * **MySQL database** running with persistent storage
  * **phpMyAdmin** to manage the database
  * **WordPress** connected to the database

* WordPress will be exposed outside the cluster. You can access it via:

```bash
kubectl get svc -n wordpress
```

Check the **EXTERNAL-IP / NodePort** and open in a browser.

---

## 📌 Flow

* **WordPress (Frontend)** → **MySQL (Database)**
* **phpMyAdmin (DB Management UI)** → **MySQL (Database)**

---

## 🎉 Result

* WordPress site deployed successfully
* Database managed via phpMyAdmin
* Both backed by Persistent Volumes for data durability


---

Do you want me to also add a **YAML tree structure** section (like `manifests/` folder with files inside) so contributors clearly see file organization?
