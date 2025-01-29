@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ minikube delete
🔥  Deleting "minikube" in docker ...
🔥  Deleting container "minikube" ...
🔥  Removing /home/codespace/.minikube/machines/minikube ...
💀  Removed all traces of the "minikube" cluster.
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ minikube start
😄  minikube v1.34.0 on Ubuntu 20.04 (docker/amd64)
✨  Automatically selected the docker driver. Other choices: none, ssh
📌  Using Docker driver with root privileges
👍  Starting "minikube" primary control-plane node in "minikube" cluster
🚜  Pulling base image v0.0.45 ...
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
🐳  Preparing Kubernetes v1.31.0 on Docker 27.2.0 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ helm repo add bitnami https://charts.bitnami.com/bitnami
"bitnami" already exists with the same configuration, skipping
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "prometheus-community" chart repository
...Successfully got an update from the "grafana" chart repository
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈Happy Helming!⎈
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ cd /workspaces/OperatorManagement
/6_Symbols/4_OperatorBitnamiConfigured/
@rifaterdemsahin ➜ /workspaces/OperatorManagement/6_Symbols/4_OperatorBitnamiConfigured (main) $ helm install grafana-a bitnami/grafana-operator -f values_a.yaml
NAME: grafana-a
LAST DEPLOYED: Wed Jan 29 13:09:23 2025
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: grafana-operator
CHART VERSION: 4.9.5
APP VERSION: 5.16.0

Did you know there are enterprise versions of the Bitnami catalog? For enhanced secure software supply chain features, unlimited pulls from Docker, LTS support, or application customization, see Bitnami Premium or Tanzu Application Catalog. See https://www.arrow.com/globalecs/na/vendors/bitnami for more information.

** Please be patient while the chart is being deployed **

Watch the Grafana Operator Deployment status using the command:

    kubectl get deploy -w --namespace default -l app.kubernetes.io/name=grafana-operator,app.kubernetes.io/instance=grafana-a


WARNING: There are "resources" sections in the chart not set. Using "resourcesPreset" is not recommended for production. For production installations, please set the following values according to your workload needs:
  - grafana.resources
  - operator.resources
+info https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
@rifaterdemsahin ➜ /workspaces/OperatorManagement/6_Symbols/4_OperatorBitnamiConfigured (main) $ helm install grafana-b bitnami/grafana-operator -f values_b.yaml
NAME: grafana-b
LAST DEPLOYED: Wed Jan 29 13:09:53 2025
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: grafana-operator
CHART VERSION: 4.9.5
APP VERSION: 5.16.0

Did you know there are enterprise versions of the Bitnami catalog? For enhanced secure software supply chain features, unlimited pulls from Docker, LTS support, or application customization, see Bitnami Premium or Tanzu Application Catalog. See https://www.arrow.com/globalecs/na/vendors/bitnami for more information.

** Please be patient while the chart is being deployed **

Watch the Grafana Operator Deployment status using the command:

    kubectl get deploy -w --namespace default -l app.kubernetes.io/name=grafana-operator,app.kubernetes.io/instance=grafana-b


WARNING: There are "resources" sections in the chart not set. Using "resourcesPreset" is not recommended for production. For production installations, please set the following values according to your workload needs:
  - grafana.resources
  - operator.resources
+info https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
@rifaterdemsahin ➜ /workspaces/OperatorManagement/6_Symbols/4_OperatorBitnamiConfigured (main) $ kubectl get pods -l app.kubernetes.io/name=grafana-operator
NAME                                                             READY   STATUS              RESTARTS   AGE
grafana-a-grafana-operator-7f86bf58b4-7f9x9                      1/1     Running             0          46s
grafana-a-grafana-operator-grafana-deployment-6f47b5c8-jx28q     0/1     Running             0          34s
grafana-b-grafana-operator-6d9d47cc69-9q4f7                      0/1     Running             0          16s
grafana-b-grafana-operator-grafana-deployment-5644ff479d-crz5n   0/1     ContainerCreating   0          16s
@rifaterdemsahin ➜ /workspaces/OperatorManagement/6_Symbols/4_OperatorBitnamiConfigured (main) $ 