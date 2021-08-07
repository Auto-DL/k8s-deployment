# k8s-deployment

<img alt="Kubernetes" src="https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white"/>

![Contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)
[![Slack](https://img.shields.io/badge/Join%20Our%20Community-Slack-blue)](https://join.slack.com/t/autodl/shared_invite/zt-qagxiwub-ywRM_oBvvF~F7YNtlBqy_Q)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.0-4baaaa.svg)](code_of_conduct.md)

Kubernetes configuration for deployment of Auto-DL.

## How to deploy

1. Configure the variables in configmap.yaml
2. Create a secrets file in `k8s/` with following contents
```
MONGODB_URI=YOUR_MONGODB_CONNECTION_STRING
JWT_SECRET=YOUR_JWT_SECRET
```
3. Apply all the `yaml` configuration using `kubectl`
```sh
cd k8s/
kubectl apply -f configmap.yaml
kubectl create secret generic autodl-secret --from-env-file=secrets
kubectl apply -f backend-deployment.yaml
kubectl apply -f backend-service.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontnend-service.yaml
kubectl apply -f ingress.yaml
```
4. Check the status of the `pods` and `services`
![running pods](assets/pod.png)
![running services](assets/svc.png)
5. You have a working [Auto-DL](https://github.com/Auto-DL/Auto-DL) deployment :tada:

> **Note:** Install [kubeval](https://kubeval.instrumenta.dev/installation/) to run the pre-commit hooks for validating the k8s yaml configuration.
