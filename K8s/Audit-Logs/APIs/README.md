# Lacework Query Language - LQL queries to detect deprecated Kubernetes API calls

Kubernetes releases 3 new versions every year. In each release, some APIs may be deprecated or removed.

Deprecated APIs are still valid but for a limited time. Typically, they result from the graduation of new API from alpha to beta to production. These deprecated APIs are scheduled to be removed in a future release.

Deleted APIs are no longer working. If a client, a user, or a workload calls a deleted API, this results in an error. 

Upgrading from one Kubernetes version to a new one requires cluster administrators to verify that API calls no longer available in the new versions are not used anymore. This can be a tedious project without access to the Kubernetes Audit Logs. The Audit Logs show all the API calls made to the Kubernetes API. If you have a **list of deleted API calls**, you could **search the Kubernetes Audit Logs** for their presence and check who is making these calls. Sounds easy if the amount of audit logs is manageable.

With lacework, you now have the 2 pieces needed to track deprecated and deleted API calls before you migrate:
* Lacework Kubernetes AUdit Logs ingestion and LQL query language
* LQL queries with the list of deleted and deprecated APIs for each version.

## How to use the LQL queries

This repository contains 2 types of queries:
1. Deprecated API calls: K8sActivityApiDeprecated123.lql, K8sActivityApiDeprecated124.lql, etc.
2. Deleted API calls: K8sActivityApiRemoved122.lql, K8sActivityApiRemoved123.lql, etc.

Each query specifies the list of APIs added or removed in one Kubernetes version:
* K8sActivityApiRemoved**122**.lql: APIs deleted in Kubernetes **1.22**
* K8sActivityApiDeprecated**123**.lql: APIs deprecated in Kubernetes **1.23**
* etc.

If you are upgrading from Kubernetes 1.22 to 1.25, you need to run the query for each new version of Kubernetes (1.23, 1.24, and 1.25):
* K8sActivityApiDeprecated123.lql
* K8sActivityApiDeprecated124.lql
* *No deprecated APIs in 1.25*
* K8sActivityApiRemoved123.lql
* K8sActivityApiRemoved124.lql
* K8sActivityApiRemoved125.lql

Here is a sample output from the query ran on GKE:

    $ lacework query run K8sActivityApiRemoved123 –start “-30d”

    {
      "CLOUD_USER": "system:kubestore-collector",
      "CLUSTER_ID": "gke-1",
      "CLUSTER_TYPE": "GKE",
      "EVENT_NAME": "WatchHorizontalpodautoscalers",
      "EVENT_OBJECT": "/horizontalpodautoscalers",
      "EVENT_SOURCE": "horizontalpodautoscalers",
      "EVENT_URI": "/apis/autoscaling/v2beta2/horizontalpodautoscalers",
      "USER_GROUPS": null,
      "USER_ID": null,
      "USER_NAME": "system:kubestore-collector"
    },
    {...



## Setup

To run the query, and to modify them, do the following:

1. Clone this repository locally
    git clone https://github.com/lacework/lql-queries.git

2. Install and configure the Lacework CLI:  [https://docs.lacework.com/cli](https://docs.lacework.com/cli)

3. Create a query and run it:
    lacework query create -f K8s/Audit-Logs/APIs/K8sActivityApiDeprecated123.lql
    lacework query run K8sActivityApiDeprecated123 --start "-1w@w" --end "@w"

For more information about LQL, check the [LQL overview](https://docs.lacework.com/lql/lql-overview).

PRs for new queries are welcome!