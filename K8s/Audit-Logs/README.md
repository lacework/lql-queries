# Lacework Query Language - LQL queries for Kubernetes Audit Logs

Lacework can ingest the Kubernetes Audit Logs for [EKS](https://docs.lacework.com/onboarding/kubernetes-audit-logs-eks) and [GKE](https://docs.lacework.com/onboarding/gke-audit-logs).

The K8s audit logs provide valuable information about all user activities and deployment of resources such as workload, RBAC, configmaps, and more. Beyond the [security visibility](https://docs.lacework.com/onboarding/kubernetes-audit-logs-overview) provided by lacework out of the box, the Kubernetes Audit Logs give you an understanding of how Kubernetes is being used in your company.

This repository gives a few examples of additional insights you can get from your Kubernetes Audit Logs once Lacework processes them:

K8s/Audit-Logs/APIs*: detect Kubernetes API calls scheduled to be deprecated or deleted in future Kubernetes versions.

To run the query, and to modify them, do the following:

1. Clone this repository locally
    git clone https://github.com/lacework/lql-queries.git

2. Install and configure the Lacework CLI:  [https://docs.lacework.com/cli](https://docs.lacework.com/cli)

3. Create a query and run it:
    lacework query create -f K8s/Audit-Logs/APIs/K8sActivityApiDeprecated123.lql
    lacework query run K8sActivityApiDeprecated123 --start "-1w@w" --end "@w"

For more information about LQL, check the [LQL overview](https://docs.lacework.com/lql/lql-overview).

PRs for new queries are welcome!