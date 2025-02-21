# Groups

Groups allow you to limit user

Define groups with specific roles for your users
* `akhq.security.default-group`: Default group for all the user even unlogged user

* `akhq.security.groups`: Groups map definition
  * `key:` a uniq key used as name if not specified
    * `  name: group-name` Group identifier
    * `roles`: Roles list for the group
    * `attributes.topics-filter-regexp`: Regexp list to filter topics available for current group
    * `attributes.connects-filter-regexp`: Regexp list to filter Connect tasks available for current group
    * `attributes.consumer-groups-filter-regexp`: Regexp list to filter Consumer Groups available for current group
    * `attributes.acls-filter-regexp`: Regexp list to filter acls available for current group

::: warning
`topics-filter-regexp`, `connects-filter-regexp`, `consumer-groups-filter-regexp` and `acls-filter-regexp` are only used when listing resources.
If you have `topics/create` or `connect/create` roles and you try to create a resource that doesn't follow the regexp, that resource **WILL** be created.
:::

::: warning
Please also set the `micronaut.security.token.jwt.signatures.secret.generator.secret` if you set a group.
If the secret is not set, the API will not enforce the group role, and the restriction is in the UI only.
:::

3 defaults group are available :
- `admin` with all right
- `reader` with only read access on all AKHQ
- `no-roles` without any roles, that force user to login

## Roles

Here is the list of available roles to use with personalized groups

- topic/read
- topic/insert
- topic/delete
- topic/config/update
- node/read
- node/config/update
- topic/data/read
- topic/data/insert
- topic/data/delete
- group/read
- group/delete
- group/offsets/update
- registry/read
- registry/insert
- registry/update
- registry/delete
- registry/version/delete
- acls/read
- connect/read
- connect/insert
- connect/update
- connect/delete
- connect/state/update
