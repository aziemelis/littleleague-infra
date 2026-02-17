minikube start \
--driver=podman \
--kubernetes-version=v1.32.5 \
--container-runtime=containerd

1. kubectl create namespace argocd
2. kubectl apply -n argocd --server-side --force-conflicts -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
3. kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
4. kubectl get svc argocd-server -n argocd -o=jsonpath='{.status.loadBalancer.ingress[0].ip}'
5. argocd admin initial-password -n argocd
6. argocd login 127.0.0.1
7. argocd account update-password (password=password)


kubectl port-forward -n obs svc/prometheus-kube-prometheus-prometheus 9090:9090
kubectl port-forward -n obs svc/prometheus-grafana 3000:80