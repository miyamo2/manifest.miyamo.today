# manifest.miyamo.today
manifest files for blogapi.miyamo.today

## Prerequirements

1. Create Kubernetes cluster
2. Install ArgoCD
3. Install Cloudflare Tunnel Ingress Controller

## Setup

1. Set Context

2. Apply Manifest
```sh
kubectl apply -f argocd.yaml -n blog
```

4. Check Status
```sh
argocd login --core
argocd app list
# output
NAME                CLUSTER                         NAMESPACE  PROJECT  STATUS     HEALTH    SYNCPOLICY  CONDITIONS   REPO                                                  PATH           TARGET
argocd/app-of-apps  https://kubernetes.default.svc  blog     <PROJECT>  <STATUS>   <HEALTH>  Auto        <CONDITIONS> https://github.com/miyamo2/manifest.miyamo.today.git  argo-installs  main
```