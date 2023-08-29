# Lacework Query Language - LQL queries useful for AWS compliance subjects and policies

These example queries can either be used to create custom policies within the Lacework platform to suit specific use-cases or provide useful data surrounding compliance specific information. 

## How to use the LQL queries

MfaCrossAccountRoleEnforced.lql

This query can be useful to list configured IAM roles that do not enforce MFA authentication or do not include an External ID. This query can also be used to create a custom policy and trigger Platform alerts.

Example output:

    $ lacework query run MfaCrossAccountRoleEnforced –start “-30d”

  {
    "ACCOUNT_ALIAS": "lwcs1",
    "ARN": "arn:aws:iam::<ACCOUNT_ID>:role/lacework_ssense_s3_assume_role",
    "COMPLIANCE_FAILURE_REASON": "Cross-Account Access Lacks External ID or MFA",
    "RESOURCE_ID": "lacework_ssense_s3_assume_role",
    "RESOURCE_KEY": "680354150194",
    "RESOURCE_REGION": "aws-global",
    "RESOURCE_TAGS": {},
    "RESOURCE_TYPE": "iam:role",
    "SERVICE": "iam"
  }



## Setup

To run these queries, and to modify them, do the following:

1. Clone this repository locally
    git clone https://github.com/lacework/lql-queries.git

2. Install and configure the Lacework CLI:  [https://docs.lacework.com/cli](https://docs.lacework.com/cli)

3. Create a query and run it:
    lacework query create -f Compliance/AWS/IAM/MfaCrossAccountRoleEnforced.lql
    lacework query run MfaCrossAccountRoleEnforced --start "-1w@w" --end "@w"

For more information about LQL, check the [LQL overview](https://docs.lacework.com/lql/lql-overview).

PRs for new queries are welcome!
