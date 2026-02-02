1. kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
2. kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
3. kubectl get svc argocd-server -n argocd -o=jsonpath='{.status.loadBalancer.ingress[0].ip}'
4. argocd admin initial-password -n argocd
5. argocd login 127.0.0.1
6. argocd account update-password (password=password)


kubectl port-forward -n obs svc/prometheus-kube-prometheus-prometheus 9090:9090
kubectl port-forward -n obs svc/prometheus-grafana 3000:80