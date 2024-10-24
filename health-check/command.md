### doc
    https://argo-cd.readthedocs.io/en/stable/operator-manual/health/

## add custom health-check for configmap
### edit configmap
    kubectl edit -n argocd cm argocd-cm
    - add following under data field
        apiVersion: v1
        kind: ConfigMap
        metadata:
            name: argocd-cm
        data:
            resource.customizations.health.ConfigMap: |
                hs = {}
                hs.status = "Healthy"
                if obj.data.TRIANGLE_COLOR == "white" then
                hs.status = "Degraded"
                hs.message = "Use a different COLOR"
                end
                return hs
