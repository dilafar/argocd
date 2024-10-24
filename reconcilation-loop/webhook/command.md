github settings > webhooks > add webhook

payloadUrl: <argocd-uri>/api/webhook
http-method: post
content-type: application/json
trigger: push

### if using self-sighned certificate need to add --insecure tag to argocd-server  under command

    kubectl -n argocd edit deploy argocd-server
    kubectl -n argocd get pod