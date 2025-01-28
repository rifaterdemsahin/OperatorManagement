
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ helm repo add bitnami https://charts.bitnami.com/bitnami
"bitnami" has been added to your repositories
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "grafana" chart repository
...Successfully got an update from the "prometheus-community" chart repository
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈Happy Helming!⎈
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ helm install my-release bitnami/grafana-operator
NAME: my-release
LAST DEPLOYED: Tue Jan 28 15:43:34 2025
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

    kubectl get deploy -w --namespace default -l app.kubernetes.io/name=grafana-operator,app.kubernetes.io/instance=my-release


WARNING: There are "resources" sections in the chart not set. Using "resourcesPreset" is not recommended for production. For production installations, please set the following values according to your workload needs:
  - grafana.resources
  - operator.resources
+info https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $  kubectl get pods -l app.kubernetes.io/name=grafana-operator
NAME                                           READY   STATUS    RESTARTS        AGE
grafana-operator-689967c5fd-hkqqx              1/1     Running   1 (2m16s ago)   111m
my-release-grafana-operator-5584584d84-l6jbq   0/1     Pending   0               62s
@rifaterdemsahin ➜ /workspaces/OperatorManagement (main) $ 