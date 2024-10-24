### get timeout.reconciliation parameter from argocd-repo-server
    kubectl -n argocd get pod
    kubectl -n argocd describe pod argocd-repo-server-5576f8d84b-whtsg | grep -i recon

### edit argocd-cm
    kubectl -n argocd get cm argocd-cm -o yaml
    kubectl -n argocd patch configmap argocd-cm --patch='{"data":{"timeout.reconciliation":"300s"}}'
    kubectl -n argocd rollout restart deploy argocd-repo-server-5576f8d84b-whtsg
    kubectl -n argocd describe pod argocd-repo-server-5576f8d84b-whtsg | grep -i recon