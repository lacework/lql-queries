# Lacework Query Language - LQL queries for your Cloud data

This is a repository of LQL queries that shows how to track events or configurations from the Cloud data ingested and processed by Lacework. These queries are NOT part of the default policies shipped by Lacework. They demonstarte how you can get more information about your cloud infrastructure from your data, including going beyond security visibility.

This repository is organized by source:

- *K8s*: Kubernetes data - See [https://docs.lacework.com/onboarding/kubernetes-security-overview#kubernetes-security-overview](Kubernetes Security Overview)
- *K8s/Audit-Logs*: Kuberenetes Audit log data - See [https://docs.lacework.com/onboarding/kubernetes-audit-logs-overview](Kubernetes Audit Logs Overview)


To run the query, and to modify them, do the following:

1. Clone this repository locally
    git clone https://github.com/lacework/lql-queries.git

2. Install and configure the Lacework CLI:  [https://docs.lacework.com/cli](https://docs.lacework.com/cli)

3. Create a query and run it:
    lacework query create -f K8s/Audit-Logs/APIs/K8sActivityApiDeprecated123.lql
    lacework query run K8sActivityApiDeprecated123 --start "-1w@w" --end "@w"

For more information about LQL, check the [https://docs.lacework.com/lql/lql-overview](LQL overview).

PRs for new queries are welcome!