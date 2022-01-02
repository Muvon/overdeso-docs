---
description: Message related methods
---

# ✉ Message

### message.conversation.list

Get all conversation sorted in chronological way for wanted user.&#x20;

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key of account starting with BC1…</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of conversations sorted in choronological order (last to old) for given account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"message.conversation.list", "params": {"username": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 939,
            "list": [
                {
                    "stat": {
                        "count": 1
                    },
                    "timestamp": 1640481174,
                    "message": {
                        "text_hex": "04222fdadf61c7fb28787d91d1392bfcf1ea8eaa4d51608ecc7faf0d8fdff4cc799277b66ba17a97f1c86469c55a4a97d1be6710360d292423d0d8d22510508344070924359c35f516e539f3fc11f42c269bdd4ae0fe61ac5b8834ab98c8116fdf7f8e8d40f03a3b8c7bc4d381f57e37c0e8186af29c57a834ce",
                        "submitted_at": 1640481174
                    },
                    "account": {
                        "height": 80460,
                        "pubkey": "BC1YLftqfn72zNPBgSm4Fkm3A69GBf6nrYWLnLrNCuscBLdjJYGjiMk",
                        "balance": 12673162,
                        "timestamp": 1637658830,
                        "profile": {
                            "timestamp": 1637660728,
                            "is_hidden": false,
                            "height": 80470,
                            "username": "Mcclain202",
                            "description": "Tough",
                            "avatar_url": "https://overdeso.com/media/avatar/dDXj5xjHPoX",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 4887427,
                            "locked": 1,
                            "watermark": 2784726509,
                            "price": 204
                        }
                    }
                },
                {
                    "stat": {
                        "count": 2
                    },
                    "timestamp": 1639613950,
                    "message": {
                        "text_hex": "046478e63e78aa196df10be3964f152524059858839ce0f271bab6bc823d2cc95b1c645ae2668aa7fc99273a64b31cfe06ee41e591187297c0620e00f5f166d2ffd5129a3e301e439141d12a9549584d90aaa629fd68da85f7b0dc488b42b7dd1f8ecc6835df36bb920eb174e84447f7460b31d14fa6c0301e7707392b7055ff54edb4c9e98628fe6a197dd50bf3538030ea1cbd94763a2c822a5c321c578fec80a9ecd5ce575693528a7322c714bf87bd4dee8bc5e6e07d5fa08b4ce4b6ba80379021022cd3c4d8ea0e54525855e04701f0",
                        "submitted_at": 1640362349
                    },
                    "account": {
                        "height": 34786,
                        "pubkey": "BC1YLgvPruTYF3R66H96g1nCq9jhewpH7k8iwjQr7WoLacby8tNZNan",
                        "balance": 143439502,
                        "timestamp": 1623940800,
                        "profile": {
                            "timestamp": 1623941286,
                            "is_hidden": false,
                            "height": 34786,
                            "username": "BitBadgesHash",
                            "description": "Public record of all badges issued on @BitBadges. This gives anyone public access to them so anyone can a) prove ownership or b) innovate on top of @BitBadges",
                            "avatar_url": "https://overdeso.com/media/avatar/QLXvsDPy7aq",
                            "reward_points": 10000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 0,
                            "locked": 0,
                            "watermark": 0,
                            "price": 0
                        }
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### message.list

Get list of messages for wanted conversation. This method requires to send reader state as reader account info and pass params to get conversation fo reader account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username of another account for getting converstion</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Pubkey of account</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of messages sorted in chronological order (last to old)

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -H 'X-Account-Username: donhardman' -s --data '[{"method":"message.list", "params": {"username": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 3,
            "list": [
                {
                    "text_hex": "041568d0e9d2fbef71cc75e5279208edc2b7eba9bc17516b6ef293e35121ab76198f97dc17021b70493a66a422dbbef14a0b4109f9e361369bf442b9011cf6d652033eed42fa606ee78e00948a10f09c49556334c82957f5e65f60934aa543dd724d1642bf6f9ec430afbb2284e0d7dfca916f36930363e2140e27427ee70c461e2bf602ce5d9e832edd70383c9f715b9537af69838bfe6819bf515e79453804906fb56ecbdc51cfc08a89a353582c06caa16335b57a24b7cf1b8c1c89ea60318bc5984b692b",
                    "submitted_at": 1621372141,
                    "is_reader": true
                },
                {
                    "text_hex": "04ab681af12e9fc9e4e885442fdb328954a9ecbd0a2b1f803e62310a2208c347887b0d32e4f60594501118fc378ef38804c2bde8c37949616122b3cfb13e6b283da7837e088341655ac5c54303b861fd1659de2c5cfe716de397168cf48c7a405e9ca6fb5143f0afbc0b3dd101c8783c001d931a729aca2aa8575b99135449a0570d65aefc518b9a3a11083fa10cf1ad668261790b3d9e98e98321f508b441b0f3f89eefd54c90d1add39fc7224c7001b3fe5cf41b092e5ef637f8a10268bbfd3cc253d380aa820bc981593a1e55f79f7bc8638903edd26d9138e4ea6a72a9db4e1bf773d724bfbf6aeb16daa1ed82f7017705bebd39c014b62eb1f1a7c07233e442",
                    "submitted_at": 1617497678,
                    "is_reader": true
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
