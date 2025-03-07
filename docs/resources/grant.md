---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "redshift_grant Resource - terraform-provider-redshift"
subcategory: ""
description: |-
  Defines access privileges for users and  groups. Privileges include access options such as being able to read data in tables and views, write data, create tables, and drop tables. Use this command to give specific privileges for a table, database, schema, function, procedure, language, or column.
---

# redshift_grant (Resource)

Defines access privileges for users and  groups. Privileges include access options such as being able to read data in tables and views, write data, create tables, and drop tables. Use this command to give specific privileges for a table, database, schema, function, procedure, language, or column.

## Example Usage

```terraform
resource "redshift_grant" "user" {
  user        = "john"
  schema      = "my_schema"
  object_type = "schema"
  privileges  = ["create", "usage"]
}

resource "redshift_grant" "group" {
  group       = "analysts"
  schema      = "my_schema"
  object_type = "schema"
  privileges  = ["usage"]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **object_type** (String) The Redshift object type to grant privileges on (one of: table, schema, database).
- **privileges** (Set of String) The list of privileges to apply as default privileges. See [GRANT command documentation](https://docs.aws.amazon.com/redshift/latest/dg/r_GRANT.html) to see what privileges are available to which object type. An empty list could be provided to revoke all privileges for this user or group

### Optional

- **group** (String) The name of the group to grant privileges on. Either `group` or `user` parameter must be set.
- **id** (String) The ID of this resource.
- **objects** (Set of String) The objects upon which to grant the privileges. An empty list (the default) means to grant permissions on all objects of the specified type. Only has effect if `object_type` is set to `table`.
- **schema** (String) The database schema to grant privileges on.
- **user** (String) The name of the user to grant privileges on. Either `user` or `group` parameter must be set.


