# Deploy gitlab-runner with helm charts
```
kubectl create ns gitlab-runner
helm install --namespace gitlab-runner gitlab-runner -f values.yaml gitlab/gitlab-runner
```