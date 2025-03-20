# manifest.miyamo.today
manifest files for blogapi.miyamo.today

## Setup

1. Set Context
```sh
gcloud container clusters get-credentials <CLUSTER_NAME> --zone <ZONE>
kubectl config get-contexts
# output
CURRENT   NAME                                   CLUSTER                                AUTHINFO                               NAMESPACE
*         gke_<PROJECT_ID>_<ZONE>_<CLUSTER_NAME> gke_<PROJECT_ID>_<ZONE>_<CLUSTER_NAME> gke_<PROJECT_ID>_<ZONE>_<CLUSTER_NAME>
```

2. Apply Manifest
```sh
kubectl apply -f argocd.yaml -n argocd
```

3. Set Namespace
```sh
argocd login --core
kubectl config set-context --current --namespace=argocd
kubectl config get-contexts
# output
CURRENT   NAME                                   CLUSTER                                AUTHINFO                               NAMESPACE
*         gke_<PROJECT_ID>_<ZONE>_<CLUSTER_NAME> gke_<PROJECT_ID>_<ZONE>_<CLUSTER_NAME> gke_<PROJECT_ID>_<ZONE>_<CLUSTER_NAME> argocd
```

4. Check Status
```sh
argocd app list
# output
NAME                CLUSTER                         NAMESPACE  PROJECT  STATUS     HEALTH    SYNCPOLICY  CONDITIONS   REPO                                                  PATH           TARGET
argocd/app-of-apps  https://kubernetes.default.svc  argocd     default  <STATUS>   <HEALTH>  Auto        <CONDITIONS> https://github.com/miyamo2/manifest.miyamo.today.git  argo-installs  main
```