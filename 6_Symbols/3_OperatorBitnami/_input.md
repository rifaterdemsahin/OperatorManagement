To install Grafana with the Grafana Operator from Bitnami using `kubectl`, follow these steps:

1. **Add the Bitnami Helm repository**:
    ```sh
    helm repo add bitnami https://charts.bitnami.com/bitnami
    ```

2. **Update your Helm repositories**:
    ```sh
    helm repo update
    ```

3. **Install the Grafana Operator**:
    ```sh
    helm install my-release bitnami/grafana-operator
    ```

4. **Verify the installation**:
    ```sh
    kubectl get pods -l app.kubernetes.io/name=grafana-operator
    ```

These commands will add the Bitnami repository, update your Helm repositories, install the Grafana Operator, and verify the installation[1](https://github.com/bitnami/charts/blob/main/bitnami/grafana-operator/README.md).

If you have any specific configurations or need further assistance, feel free to ask!