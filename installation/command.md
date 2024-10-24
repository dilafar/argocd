### argocd documentation
    https://argo-cd.readthedocs.io/en/stable/getting_started/

### install argocd
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

### specific non-ha version install
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.12.6/manifests/install.yaml

### change service type to nodeport arocd-server
    kubectl -n argocd edit svc argocd-server
    kubectl get svc -n argocd
    kubectl get secret -n argocd
    kubectl -n argocd get secret argocd-initial-admin-secret -o json | jq .data.password -r | base64 -d

### note: username: admin
### note: once loged in update the password 

### install argocd cli
    wget https://github.com/argoproj/argo-cd/releases/download/v2.12.6/argocd-linux-amd64
    mv argocd-linux-amd64 argocd
    chmod +x argocd
    mv argocd /usr/local/bin/
    argocd

### login using argocdcli (get argocd-server ip)
    kubectl get svc -n argocd
    argocd login 10.98.110.228
    argocd app list
    argocd cluster list

## 
    argocd proj list
    argocd -n argocd get applications
    argocd -n argocd get appproj