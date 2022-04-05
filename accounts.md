# Accounts

## List accounts

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts?auth_method_id=ampw_1234567890 \
-H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
  "items": [
    {
      "id": "acctpw_0987654321",
      "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
      },
      "created_time": "2022-04-05T09:24:54.263583Z",
      "updated_time": "2022-04-05T09:24:54.263583Z",
      "version": 1,
      "type": "password",
      "auth_method_id": "ampw_1234567890",
      "attributes": {
        "login_name": "user"
      },
      "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
      ]
    },
    {
      "id": "acctpw_1234567890",
      "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
      },
      "created_time": "2022-04-05T09:24:54.481610Z",
      "updated_time": "2022-04-05T09:24:54.481610Z",
      "version": 1,
      "type": "password",
      "auth_method_id": "ampw_1234567890",
      "attributes": {
        "login_name": "admin"
      },
      "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
      ]
    }
  ]
}
```

## Create account

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts \
    -H "Authorization: Bearer ${TOKEN}" \
    -d '{"attributes":{"login_name":"devops-rob-account"},"auth_method_id":"ampw_1234567890"}' \
    -X POST
```

Sample payload

```json
{
    "attributes":{
        "login_name": "devops-rob-account"
    },
    "auth_method_id": "ampw_1234567890"

}
```

Sample response

```json
{
    "id": "acctpw_F6KHknKdk4",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "created_time": "2022-04-05T11:05:18.627571Z",
    "updated_time": "2022-04-05T11:05:18.627571Z",
    "version": 1,
    "type": "password",
    "auth_method_id": "ampw_1234567890",
    "attributes": {
        "login_name": "devops-rob-account"
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
    ]
}
```

## Get account

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts/acctpw_F6KHknKdk4 \
    -H "Authorization: Bearer ${TOKEN}"
```

> _**NOTE: The http endpoint must include the account ID. In this example this is `acctpw_F6KHknKdk4`.**_

Sample response

```json
{
    "id": "acctpw_F6KHknKdk4",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "created_time": "2022-04-05T11:05:18.627571Z",
    "updated_time": "2022-04-05T11:05:18.627571Z",
    "version": 1,
    "type": "password",
    "auth_method_id": "ampw_1234567890",
    "attributes": {
        "login_name": "devops-rob-account"
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
    ]
}
```

## Delete account

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts/acctpw_F6KHknKdk4 \
    -H "Authorization: Bearer ${TOKEN}" \
    -X DELETE
```

## Update account

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts/acctpw_F6KHknKdk4 \
    -H "Authorization: Bearer ${TOKEN}" \
    -X PATCH
```

Sample payload

```json
{
    "name": "Rob Barnes",
    "version": 1
}
```

> _**NOTE: The version of the resource is auto-generated and can be obtained using the `get account` API call.**_

Sample response

```json
{
    "id": "acctpw_ik2FD38WEF",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "name": "Rob Barnes",
    "created_time": "2022-04-05T11:20:28.576423Z",
    "updated_time": "2022-04-05T11:24:11.354112Z",
    "version": 2,
    "type": "password",
    "auth_method_id": "ampw_1234567890",
    "attributes": {
        "login_name": "devops-rob-account"
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
    ]
}
```

## Set account password

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts/acctpw_ik2FD38WEF:set-password \
    -H "Authorization: Bearer ${TOKEN}" \
    -X POST
```

Sample payload

```json
{
    "password": "password",
    "version": 2
}
```

Sample response

```json
{
    "id": "acctpw_ik2FD38WEF",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "name": "Rob Barnes",
    "created_time": "2022-04-05T11:20:28.576423Z",
    "updated_time": "2022-04-05T12:20:27.114869Z",
    "version": 3,
    "type": "password",
    "auth_method_id": "ampw_1234567890",
    "attributes": {
        "login_name": "devops-rob-account"
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
    ]
}
```

## Change account password

Sample cURL request

```shell
curl http://localhost:9200/v1/accounts/acctpw_ik2FD38WEF:change-password \
    -H "Authorization: Bearer ${TOKEN}" \
    -X POST
```

Sample payload

```json
{
    "current_password": "password",
    "new_password": "new-password",
    "version": 3
}
```

Sample response

```json
{
    "id": "acctpw_ik2FD38WEF",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "name": "Rob Barnes",
    "created_time": "2022-04-05T11:20:28.576423Z",
    "updated_time": "2022-04-05T12:24:20.447169Z",
    "version": 4,
    "type": "password",
    "auth_method_id": "ampw_1234567890",
    "attributes": {
        "login_name": "devops-rob-account"
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "set-password",
        "change-password"
    ]
}
```
