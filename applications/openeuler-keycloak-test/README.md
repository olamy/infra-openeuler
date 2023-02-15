Actions to deploy keycloak in Kubernetes cluster
---

Create a dedicated namespace
---
```shell
kubectl create namespace keycloak
```

Creating secrets
---

Mysql secrets
```shell
kubectl create secret generic -n keycloak mysql-secret --from-literal=root_password= --from-literal=user_password=
```
Keycloak secrets
```shell
kubectl create secret generic -n keycloak keycloak-secret --from-literal=admin_password=
```

Deploy mysql instance with persistent volume
---

Please note and size might be adjust for production environment

```shell
kubectl apply -f mysql-pv.yaml
kubectl apply -f mysql-deployment.yaml
```
Deploy Keycloak app with Ingress

```shell
kubectl apply -f keycloak-deployment.yaml
kubectl apply -f keycloak-ingress.yaml
```