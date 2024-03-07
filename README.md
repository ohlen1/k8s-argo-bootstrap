# k8s-argo-bootstrap

This is an example of a way to setup basic services in a typical Kubernetes cluster using [ArgoCD](https://argo-cd.readthedocs.io/), using the *app of apps* pattern. In this case it will create an Argo app named bootstrap-app, that in turn sets up Argo apps for the following services from official Helm repos:
* [Cluster Autoscaler](https://github.com/kubernetes/autoscaler)
* [Ingress NGINX](https://github.com/kubernetes/ingress-nginx)
* [Prometheus Stack](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack)

## Install
Up and running in notime!

Assuming you have a Kubernetes cluster up and running, follow the below steps. If not you can easily spin up a local Kind cluster for testing in less than 5 minutes. See [here](https://kind.sigs.k8s.io/docs/user/quick-start/#installation) on how to.

1. Install ArgoCD:
   ```bash
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```

2. Install the bootstrap-app:
   ```bash
   kubectl apply -f bootstrap-app.yaml -n argocd
   ```