### create application using argocli
    argocd app create color-app \
    --repo https://github.com/sid/app-1.git \
    --path team-a/color \
    --dest-namespace color \
    --dest-server https://kubernetes.default.svc

### list app
    argocd app list

### synchronize application
    argocd app sync color-app
    argocd app list