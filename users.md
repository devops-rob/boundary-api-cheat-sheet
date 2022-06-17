# Users

## List users

Sample cURL request

```shell
curl http://localhost:9200/v1/users?scope_id=${SCOPE_ID}&recursive=true \
    -X GET \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
    "items": [
        {
            "id": "u_anon",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "anonymous",
            "description": "The anonymous user matches any request, whether authenticated or not",
            "created_time": "2022-06-16T07:40:08.205855Z",
            "updated_time": "2022-06-16T07:40:08.205855Z",
            "version": 1,
            "authorized_actions": [
                "no-op",
                "read",
                "update",
                "delete",
                "add-accounts",
                "set-accounts",
                "remove-accounts"
            ]
        },
        {
            "id": "u_auth",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "authenticated",
            "description": "The authenticated user matches any user that has a valid token",
            "created_time": "2022-06-16T07:40:08.205855Z",
            "updated_time": "2022-06-16T07:40:08.205855Z",
            "version": 1,
            "authorized_actions": [
                "no-op",
                "read",
                "update",
                "delete",
                "add-accounts",
                "set-accounts",
                "remove-accounts"
            ]
        },
        {
            "id": "u_recovery",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "recovery",
            "description": "The recovery user is used for any request that was performed with the recovery KMS workflow",
            "created_time": "2022-06-16T07:40:08.205855Z",
            "updated_time": "2022-06-16T07:40:08.205855Z",
            "version": 1,
            "authorized_actions": [
                "no-op",
                "read",
                "update",
                "delete",
                "add-accounts",
                "set-accounts",
                "remove-accounts"
            ]
        },
        {
            "id": "u_1234567890",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "admin",
            "description": "Initial admin user within the \"global\" scope",
            "created_time": "2022-06-16T07:40:10.229139Z",
            "updated_time": "2022-06-16T07:40:10.318365Z",
            "version": 3,
            "authorized_actions": [
                "no-op",
                "read",
                "update",
                "delete",
                "add-accounts",
                "set-accounts",
                "remove-accounts"
            ],
            "login_name": "admin",
            "primary_account_id": "acctpw_1234567890"
        },
        {
            "id": "u_0987654321",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "user",
            "description": "Initial unprivileged user",
            "created_time": "2022-06-16T07:40:09.999316Z",
            "updated_time": "2022-06-16T07:40:10.346021Z",
            "version": 3,
            "authorized_actions": [
                "no-op",
                "read",
                "update",
                "delete",
                "add-accounts",
                "set-accounts",
                "remove-accounts"
            ],
            "login_name": "user",
            "primary_account_id": "acctpw_0987654321"
        },
        {
            "id": "u_EVJg79MbMv",
            "scope_id": "o_1234567890",
            "scope": {
                "id": "o_1234567890",
                "type": "org",
                "name": "Generated org scope",
                "description": "Provides an initial org scope in Boundary",
                "parent_scope_id": "global"
            },
            "name": "devopsrob",
            "description": "An example user for DevOps Rob",
            "created_time": "2022-06-16T07:48:35.861613Z",
            "updated_time": "2022-06-16T07:48:35.861613Z",
            "version": 1,
            "authorized_actions": [
                "no-op",
                "read",
                "update",
                "delete",
                "add-accounts",
                "set-accounts",
                "remove-accounts"
            ]
        }
    ]
}
```

## Create User

Sample cURL request

```shell
curl http://localhost:9200/v1/users \
    -X POST \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "scope_id": "o_1234567890",
    "name": "devopsrob",
    "description": "An example user for DevOps Rob"
}
```

Sample response

```json
{
    "id": "u_EVJg79MbMv",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "devopsrob",
    "description": "An example user for DevOps Rob",
    "created_time": "2022-06-16T07:48:35.861613Z",
    "updated_time": "2022-06-16T07:48:35.861613Z",
    "version": 1,
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "add-accounts",
        "set-accounts",
        "remove-accounts"
    ]
}
```

## Get User

Sample cURL request

```shell
curl http://localhost:9200/v1/users/${USER_ID} \
    -X GET \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
    "id": "u_EVJg79MbMv",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "devopsrob",
    "description": "An example user for DevOps Rob",
    "created_time": "2022-06-16T07:48:35.861613Z",
    "updated_time": "2022-06-16T07:48:35.861613Z",
    "version": 1,
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "add-accounts",
        "set-accounts",
        "remove-accounts"
    ]
}
```

## Delete User

Sample cURL request

```shell
curl http://localhost:9200/v1/users/${USER_ID} \
    -X DELETE \   
    -H "Authorization: Bearer ${TOKEN}"
```

## Update User

Sample cURL request

```shell
curl http://localhost:9200/v1/users/${USER_ID} \
    -X PATCH \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "scope_id": "o_1234567890",
    "name": "devopsrob",
    "description": "An UPDATED example user for DevOps Rob",
    "version": 1
}
```

Sample response

```json
{
    "id": "u_EVJg79MbMv",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "devopsrob",
    "description": "An UPDATED example user for DevOps Rob",
    "created_time": "2022-06-16T07:48:35.861613Z",
    "updated_time": "2022-06-16T08:33:12.041728Z",
    "version": 2,
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "add-accounts",
        "set-accounts",
        "remove-accounts"
    ]
}
```

## Add user accounts

Sample cURL request

```shell
curl http://localhost:9200/v1/users/${USER_ID}:add-accounts \
    -X POST \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "version": 2,
    "account_ids": [
        "acctpw_WGopb9Aicq"
    ]
}
```

Sample response

```json
{
    "id": "u_bouhEbeEbT",
    "scope_id": "global",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "name": "devopsrob",
    "created_time": "2022-06-17T09:02:09.389717Z",
    "updated_time": "2022-06-17T09:04:04.231453Z",
    "version": 2,
    "account_ids": [
        "acctpw_Ms088e7TQd"
    ],
    "accounts": [
        {
            "id": "acctpw_Ms088e7TQd",
            "scope_id": "global"
        }
    ],
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "add-accounts",
        "set-accounts",
        "remove-accounts"
    ],
    "login_name": "devopsrob",
    "primary_account_id": "acctpw_Ms088e7TQd"
}
```


## Remove accounts

Sample cURL request

```shell
curl http://localhost:9200/v1/users/${USER_ID}:remove-accounts \
    -X POST \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "version": 3,
    "account_ids": [
        "acctpw_WGopb9Aicq"
    ]
}
```

Sample response

```json
{
    "id": "u_bouhEbeEbT",
    "scope_id": "global",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "name": "devopsrob",
    "created_time": "2022-06-17T09:02:09.389717Z",
    "updated_time": "2022-06-17T09:06:43.945111Z",
    "version": 3,
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "add-accounts",
        "set-accounts",
        "remove-accounts"
    ]
}
```

## Set accounts

Sample cURL request

```shell
curl http://localhost:9200/v1/users/${USER_ID}:set-accounts \
    -X POST \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "version": 3,
    "account_ids": [
        "acctpw_WGopb9Aicq"
    ]
}
```

Sample response

```json
{
    "id": "u_bouhEbeEbT",
    "scope_id": "global",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "name": "devopsrob",
    "created_time": "2022-06-17T09:02:09.389717Z",
    "updated_time": "2022-06-17T09:12:14.452884Z",
    "version": 4,
    "account_ids": [
        "acctpw_Ms088e7TQd"
    ],
    "accounts": [
        {
            "id": "acctpw_Ms088e7TQd",
            "scope_id": "global"
        }
    ],
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "add-accounts",
        "set-accounts",
        "remove-accounts"
    ],
    "login_name": "devopsrob",
    "primary_account_id": "acctpw_Ms088e7TQd"
}
```
