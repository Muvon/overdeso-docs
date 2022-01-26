---
description: Message related methods
---

# ✉ Message

### message.conversation.list

Get all conversation sorted in chronological way for wanted user.&#x20;

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of conversations sorted in choronological order (last to old) for given account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"message.conversation.list", "params": {"account": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 235,
            "list": [
                {
                    "stat": {
                        "message_count": 1,
                        "member_count": 2
                    },
                    "timestamp": 1617289499,
                    "message": {
                        "text_hex": "04c782cce5b85a846ed2ff93f2fbf43eb52cdf64b57ec9e928393ace802496627755cfa4bb80c8e999aecffe989337aa5d38a216511d9904631d91f8dddbd4cc940d3cb567787b91c3648ec970ce4472fab8a47471d8bea149377cbaa2e1dbb5b909c041d385c1ff3fd8069f966b7ab1c390e9df201940518b4b187e40225f5dce4c9c258a8d62226c83eb00152c5058dfe152819472479834875ac4dbe3ec6415d78e623d2a35525b4d4c7ea896ea8985663061d02fbc1808372280892ba2e9e662b9c1b5d800a90d9424828da3387938a23658b0b7ea5b72d316e782a832614161840c28964a535c1f3217634aca5c29e1ffa53d6a61b22941df4809fddb17175b244adb0596bdf4a3c9ce3273ecd33426100b9acab10b0b483dc6c140b1d9dd682463708bab932ba0e4356521dd7353d2afbad11a032c01b54518448fbe36d336c1",
                        "submitted_at": 1617289499,
                        "is_reader": false,
                        "version": 1
                    },
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 4588895657,
                        "timestamp": 1615574505,
                        "profile": {
                            "timestamp": 1615574830,
                            "is_hidden": false,
                            "height": 6043,
                            "username": "diamondhands",
                            "description": "💎🙌",
                            "avatar_url": "http://media.overdeso.lo/avatar/Xs8QAFT7gy4",
                            "reward_points": 0,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 251018488621,
                            "locked": 15816770607695,
                            "watermark": 255810788786,
                            "price": 63010381006
                        }
                    }
                },
                {
                    "stat": {
                        "message_count": 13,
                        "member_count": 2
                    },
                    "timestamp": 1616889860,
                    "message": {
                        "text_hex": "045b25eb8efe7d6af3645a8bb3e77259d4b592564b5c83784d795e016471aaffaefef286d72728826d8262181bf4427f70990383414e75927105c48eae5de782a4cf6c0c6099e4f251e998c15fc40c8fd61488acea252a0cd3bc884c34e3231fa0de23a8398f2ab0cca76141ca509168a3b644561aa78bbab8e3ea2fb542ab71f89a36ef0ff60e078a0baeed3ec4abf0ab6c8277d2dde90b34a99eff2c28e3f2c0ef3eacd1a59aec4a1700c76a049e1dfb9b8ec5154028b5fbdcb25e7ef5f38ef1fb5fa59367529dec1a4e6cf77d3a9bfe45440370abb31c1e58d342bd0263856a6562f8e7b545bfd68367964146b478b409078f1185f33cedddc4c76e372aa3c7edb17b8d35247293d56057eabbed63b834df766fbb1f2367ec997b5cba891f5eea5a595211cd72495a861abe2868c048e87b127b8201d57d71967f978ac6caeec2dc1fe93d5d4b48edf902182098e87a1609018cffd75ed3952d6900008d4cd1a20d2a4e190fe9830f385494b8b41bc76429e6d7689ea91d08d7636554ce8e7cd7ae4e95d6171b6bb054f76c079077db09b75a7240b166277a0be6f986ff6f",
                        "submitted_at": 1617287440,
                        "is_reader": false,
                        "version": 1
                    },
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 4588895657,
                        "timestamp": 1615574505,
                        "profile": {
                            "timestamp": 1615574830,
                            "is_hidden": false,
                            "height": 6043,
                            "username": "diamondhands",
                            "description": "💎🙌",
                            "avatar_url": "http://media.overdeso.lo/avatar/Xs8QAFT7gy4",
                            "reward_points": 0,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 251018488621,
                            "locked": 15816770607695,
                            "watermark": 255810788786,
                            "price": 63010381006
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

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of messages sorted in chronological order (last to old)

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -H 'X-Reader-Account: donhardman' -s --data '[{"method":"message.list", "params": {"account": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
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
