# Auth Token

## List Auth Tokens

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-tokens?scope_id=global&recursive=true \
    -H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
    "items": [
        {
            "id": "at_YvTucC25Eg",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "user_id": "u_1234567890",
            "auth_method_id": "ampw_1234567890",
            "account_id": "acctpw_1234567890",
            "created_time": "2022-04-14T14:17:26.895854Z",
            "updated_time": "2022-04-14T14:17:26.895854Z",
            "approximate_last_used_time": "2022-04-14T14:17:26.895854Z",
            "expiration_time": "2022-04-21T14:17:26Z",
            "authorized_actions": [
                "no-op",
                "read",
                "read:self",
                "delete",
                "delete:self"
            ]
        },
        {
            "id": "at_9J6BTpHUAy",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "user_id": "u_1234567890",
            "auth_method_id": "ampw_1234567890",
            "account_id": "acctpw_1234567890",
            "created_time": "2022-04-22T09:34:40.246581Z",
            "updated_time": "2022-04-22T09:53:52.927245Z",
            "approximate_last_used_time": "2022-04-22T09:53:52.927245Z",
            "expiration_time": "2022-04-29T09:34:40Z",
            "authorized_actions": [
                "no-op",
                "read",
                "read:self",
                "delete",
                "delete:self"
            ]
        },
        {
            "id": "at_aIkM0QUTmA",
            "scope_id": "global",
            "scope": {
                "id": "global",
                "type": "global",
                "name": "global",
                "description": "Global Scope"
            },
            "user_id": "u_1234567890",
            "auth_method_id": "ampw_1234567890",
            "account_id": "acctpw_1234567890",
            "created_time": "2022-04-22T09:50:18.050933Z",
            "updated_time": "2022-04-22T12:07:46.719942Z",
            "approximate_last_used_time": "2022-04-22T12:07:46.719942Z",
            "expiration_time": "2022-04-29T09:50:18Z",
            "authorized_actions": [
                "no-op",
                "read",
                "read:self",
                "delete",
                "delete:self"
            ]
        }
    ]
}
```

## Get Auth Token

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-tokens/at_aIkM0QUTmA \
    -H "Authorization: Bearer ${TOKEN}"
```

Sample response

```json
{
    "id": "at_aIkM0QUTmA",
    "scope_id": "global",
    "scope": {
        "id": "global",
        "type": "global",
        "name": "global",
        "description": "Global Scope"
    },
    "user_id": "u_1234567890",
    "auth_method_id": "ampw_1234567890",
    "account_id": "acctpw_1234567890",
    "created_time": "2022-04-22T09:50:18.050933Z",
    "updated_time": "2022-04-22T12:07:46.719942Z",
    "approximate_last_used_time": "2022-04-22T12:07:46.719942Z",
    "expiration_time": "2022-04-29T09:50:18Z",
    "authorized_actions": [
        "no-op",
        "read",
        "read:self",
        "delete",
        "delete:self"
    ]
}
```

## Delete Auth Token

Sample cURL request

```shell
curl http://localhost:9200/v1/auth-tokens/at_aIkM0QUTmA \
    -H "Authorization: Bearer ${TOKEN}" \
    -X DELETE
```

Sample response

This returns a 200 code with no response body.
