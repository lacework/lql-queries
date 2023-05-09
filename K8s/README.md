# Lacework Query Language - LQL queries for Kubernetes

These queries run on the Kubernetes data collected by Lacework.

- *K8s/Audit-Logs*: Kuberenetes Audit log data - See [Kubernetes Audit Logs Overview](https://docs.lacework.com/onboarding/kubernetes-audit-logs-overview)
- *K8s/Audit-Logs/APIs*: detect Kubernetes API calls scheduled to be deprecated or deleted in future Kubernetes versions.

To run the query, and to modify them, do the following:

1. Clone this repository locally
    git clone https://github.com/lacework/lql-queries.git

2. Install and configure the Lacework CLI:  [https://docs.lacework.com/cli](https://docs.lacework.com/cli)

3. Create a query and run it:
    lacework query create -f K8s/Audit-Logs/APIs/K8sActivityApiDeprecated123.lql
    lacework query run K8sActivityApiDeprecated123 --start "-1w@w" --end "@w"

For more information about LQL, check the [LQL overview](https://docs.lacework.com/lql/lql-overview).

PRs for new queries are welcome!