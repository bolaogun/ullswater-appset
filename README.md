# ullswater-argo-appset

## Bootstrap the Stack 
Install cluster, get it running & ensure it is your current context

For minikube try:
`minikube start --cpus 4 --memory 8192 --disk-size=50g --driver=docker --kubernetes-version=v1.21.0`

Install Argocd thus:
```
kubectl create ns argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get secrets argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode ; echo
kubectl port-forward -n argocd svc/argocd-server 8080:443 > /dev/null 2>&1 &
kubectl apply -f application.yaml
```

Navigate to https://localhost:8080/applications & use "admin" as the username along with the secret retrieved aralier

