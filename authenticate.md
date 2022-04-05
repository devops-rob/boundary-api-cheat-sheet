# Boundary API Cheat Sheet

This repository contains examples of interacting with the HashiCorp Boundary API using cURL.

1. [Authentication](#authenticate-to-boundary)
2. [Accounts](accounts.md)

## Authenticate to Boundary

Sample cURL command

```shell
curl -X POST http://localhost:9200/v1/auth-methods/ampw_1234567890:authenticate
```

> _**NOTE: The http endpoint must include the auth-method ID. In this example this is `ampw_1234567890`.**_

Sample payload

```json
{
    "attributes": {
        "login_name": "admin",
        "password": "password"
    }
}
```

Sample response

```json
{
    "attributes": {
        "account_id": "acctpw_1234567890",
        "approximate_last_used_time": "2022-04-05T09:48:47.771090Z",
        "auth_method_id": "ampw_1234567890",
        "authorized_actions": [
            "read:self",
            "delete:self"
        ],
        "created_time": "2022-04-05T09:48:47.771090Z",
        "expiration_time": "2022-04-12T09:48:47Z",
        "id": "at_J6mC5I3grZ",
        "scope": {
            "id": "global",
            "type": "global"
        },
        "token": "at_J6mC5I3grZ_s16GTWmeRiBdsTcQ29V2RMkefDfx8LPTro1feFhxuhi1srhtLeQJSLCyZNQ7iMiKCQwfqZr4yEx4RAth6rZUTnBNS9gdt6BMJZKbJAYg7vCHSo7Vfb77qKSot1vURb7z3uLoMFKkK",
        "token_type": "",
        "updated_time": "2022-04-05T09:48:47.771090Z",
        "user_id": "u_1234567890"
    },
    "command": "login"
}
```

The token value in the response can be used for all future API calls to boundary by storing this in an environment variable using JQ.

```shell
TOKEN="$(curl -X POST http://localhost:9200/v1/auth-methods/ampw_1234567890:authenticate -d '{"attributes":{"login_name":"admin","password":"password"}}'| jq -r '.attributes.token')"
```

> _**NOTE: All future API call examples will use `$TOKEN` as the bearer token.**_
