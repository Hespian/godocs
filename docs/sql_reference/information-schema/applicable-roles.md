---
layout: default
title: Applicable roles
description: Use this reference to learn about the metadata available about roles using the information schema.
parent: Information schema
grand_parent: SQL reference
---

# Information schema for applicable_roles

You can use the `information_schema.applicable_roles` view to return information about roles available in the account.
You can use a `SELECT` query to return information about each role as shown in the example below.
```sql
SELECT
  *
FROM
  information_schema.applicable_roles;
```

{: .note}
Read more about RBAC roles [here](../../Guides/managing-your-organization/rbac.md).

## Columns in information_schema.applicable_roles

Each row has the following columns with information about the role.

|  Column Name    | Data Type | Description                                                     |
|:----------------|:----------|:----------------------------------------------------------------|
| grantee         | TEXT      | Role or user to whom the privilege is granted (TO USER\|ROLE).  |
| role_name       | TEXT      | Name of the role.                                               |
| is_grantable    | TEXT      | YES if the grantee has the admin option on the role, NO if not. |
| description     | TEXT      | Description of the role.                                        |
| created         | TIMESTAMPTZ | Creation time of the role.                                      |
| role_owner      | TEXT      | Name of the user that created the role.                         |
| last_altered    | TIMESTAMPTZ | Time the role was last altered.                                 |
| last_altered_by | TEXT      | Name of the last user to edit the role.                         |
