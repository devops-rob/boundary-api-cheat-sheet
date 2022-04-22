# Auth Method

## List Auth Methods

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-methods?scope_id=global \
    -H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
    "items": [
        {
            "id": "amoidc_1234567890",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "Generated global scope initial oidc auth method",
            "description": "Provides initial administrative and unprivileged authentication into Boundary",
            "type": "oidc",
            "authorized_actions": [
                "authenticate"
            ]
        },
        {
            "id": "ampw_1234567890",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "name": "Generated global scope initial password auth method",
            "description": "Provides initial administrative and unprivileged authentication into Boundary",
            "type": "password",
            "is_primary": true,
            "authorized_actions": [
                "authenticate"
            ]
        }
    ]
}
```

## Create Auth Method

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-methods \
    -X POST \
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "scope_id": "o_1234567890",
    "name": "developers_ampw",
    "type": "password"
}
```

Sample response

```json
{
    "id": "ampw_0bneiIdfA8",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "developers_ampw",
    "created_time": "2022-04-22T09:51:48.864332Z",
    "updated_time": "2022-04-22T09:51:48.864332Z",
    "version": 1,
    "type": "password",
    "attributes": {
        "min_login_name_length": 3,
        "min_password_length": 8
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "authenticate"
    ],
    "authorized_collection_actions": {
        "accounts": [
            "create",
            "list"
        ],
        "managed-groups": [
            "create",
            "list"
        ]
    }
}
```

## Get Auth Method

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-methods/ampw_0bneiIdfA8 \
    -H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
    "id": "ampw_0bneiIdfA8",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "developers_ampw",
    "created_time": "2022-04-22T09:51:48.864332Z",
    "updated_time": "2022-04-22T09:51:48.864332Z",
    "version": 1,
    "type": "password",
    "attributes": {
        "min_login_name_length": 3,
        "min_password_length": 8
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "authenticate"
    ],
    "authorized_collection_actions": {
        "accounts": [
            "create",
            "list"
        ],
        "managed-groups": [
            "create",
            "list"
        ]
    }
}
```

## Update Auth Method

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-methods/ampw_0bneiIdfA8 \
    -H "Authorization: Bearer ${TOKEN}"
    -X PATCH
```

Sample payload

```json
{
    "name": "HashiCorp Dev Advocates",
    "version": 1
}
```

Sample response

```json
{
    "id": "ampw_0bneiIdfA8",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "HashiCorp Dev Advocates",
    "created_time": "2022-04-22T09:51:48.864332Z",
    "updated_time": "2022-04-22T10:31:35.966351Z",
    "version": 2,
    "type": "password",
    "attributes": {
        "min_login_name_length": 3,
        "min_password_length": 8
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "authenticate"
    ],
    "authorized_collection_actions": {
        "accounts": [
            "create",
            "list"
        ],
        "managed-groups": [
            "create",
            "list"
        ]
    }
}
```

## Change state

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-methods/amoidc_vGGSJDyQx6:change-state \
    -X POST \   
    -H "Authorization: Bearer ${TOKEN}"
```

Sample payload

```json
{
    "version": 1,
    "attributes": {
        "state": "inactive"
    }
}
```

Sample response

```json
{
    "id": "amoidc_vGGSJDyQx6",
    "scope_id": "o_1234567890",
    "scope": {
        "id": "o_1234567890",
        "type": "org",
        "name": "Generated org scope",
        "description": "Provides an initial org scope in Boundary",
        "parent_scope_id": "global"
    },
    "name": "EU-OIDC",
    "created_time": "2022-04-22T11:43:49.470872Z",
    "updated_time": "2022-04-22T11:43:49.470872Z",
    "version": 1,
    "type": "oidc",
    "attributes": {
        "api_url_prefix": "https://something.com",
        "callback_url": "https://something.com/v1/auth-methods/oidc:authenticate:callback",
        "client_id": "id",
        "client_secret_hmac": "PBPGMwO3LhaOxjtsjAL2K71Z4peoJevhtMBRUm-h-ww",
        "state": "inactive"
    },
    "authorized_actions": [
        "no-op",
        "read",
        "update",
        "delete",
        "change-state",
        "authenticate"
    ],
    "authorized_collection_actions": {
        "accounts": [
            "create",
            "list"
        ],
        "managed-groups": [
            "create",
            "list"
        ]
    }
}
```

## Delete Auth Method

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-methods/ampw_0bneiIdfA8 \
    -H "Authorization: Bearer ${TOKEN}" \
    -X DELETE
```

Sample response

```json
{}
```
