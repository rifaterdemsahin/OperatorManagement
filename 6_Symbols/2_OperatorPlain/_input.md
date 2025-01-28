# Tomi implementation Gpt Generated
- minikube delete
- minikube start
- helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
- helm repo update
- kubectl create namespace grafana-monitoring 

- helm repo add grafana https://grafana.github.io/helm-charts
- helm repo update
# uses the default value as it is an operator 
- helm install grafana-operator grafana/grafana-operator  -n default

# prometheus stak depends on the grafana-operator CRD
- helm install prometheus-operator prometheus-community/kube-prometheus-stack -n default
# in the back ground it installs the grafana service
- kubectl get pods -n default

# GrafanaOperator should be used to deploy datasource > this is controlled by the operator based
- kubectl get pods -n grafana-monitoring
- kubectl get all -n grafana-monitoring

# GrafanaInstance
- kubectl apply -f /workspaces/OperatorManagement/6_Symbols/2_Operator/datasource.yaml -n grafana-monitoring
- kubectl get pods -n grafana-monitoring
