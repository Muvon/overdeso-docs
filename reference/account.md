---
description: Account related API methods.
---

# 👤 Account

### account.get

The method allows to get profile by username or account by public key in base58 check format.

The method requires one of **username** or **pubkey** to be passed in request body.

#### Request params <a href="#request-params" id="request-params"></a>

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr></tbody></table>

#### Response

The method returns account stracture with fields: pubkey, height, profile, coin, stat.

{% tabs %}
{% tab title="CURL" %}
```shell
curl --data '[{"method":"account.get", "params": {"account":"diamondhands"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "height": 6042,
            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
            "balance": 1202557738544,
            "timestamp": 1615574505,
            "profile": {
                "timestamp": 1615574830,
                "is_hidden": false,
                "height": 6043,
                "username": "diamondhands",
                "description": "💎🙌",
                "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                "reward_points": 0,
                "stake_points": 12500
            },
            "coin": {
                "supply": 164217523869,
                "locked": 4578709213058,
                "watermark": 255810788786,
                "price": 27881976936
            },
            "stat": {
                "last_stat_ts": 1641133448,
                "utxo_count": 5471,
                "holder_count": 3684,
                "holding_count": 2663,
                "follower_count": 23962,
                "following_count": 31,
                "coin_buy_count": 81,
                "coin_buy_value": 8611846815339,
                "coin_sell_count": 2,
                "coin_sell_value": 60683183,
                "coin_gain": -835936510603,
                "sender_connection_count": 943,
                "sender_connection_value": 769238278576,
                "receiver_connection_count": 69664,
                "receiver_connection_value": 131603196418987,
                "sender_seed_count": 1,
                "sender_seed_value": 300000000000,
                "receiver_seed_count": 2,
                "receiver_seed_value": 100000000,
                "sender_coin_count": 1644,
                "sender_coin_value": 835936498462,
                "receiver_coin_count": 9265,
                "receiver_coin_value": 619827916700,
                "reward_coins": 0,
                "reward_value": 0,
                "sender_diamond_count": 6463,
                "sender_diamond_value": 101771508175,
                "receiver_diamond_count": 29474,
                "receiver_diamond_value": 155715519222,
                "post_count": 89,
                "repost_count": 8,
                "quote_count": 34,
                "comment_count": 565,
                "sender_post_like_count": 82,
                "receiver_post_like_count": 70552,
                "nft_count": 0,
                "nft_royalty": 0,
                "nft_coin": 117500000000,
                "nft_mint_count": 2,
                "nft_mint_value": 467500000000,
                "nft_buy_count": 12,
                "nft_buy_value": 51738588404,
                "nft_sell_count": 0,
                "nft_sell_value": 0,
                "nft_gain": 467500000000,
                "sender_nft_bid_count": 0,
                "receiver_nft_bid_count": 152,
                "sender_message_count": 99,
                "recipient_message_count": 2306,
                "sender_conversation_count": 10,
                "recipient_conversation_count": 929,
                "conversation_count": 939,
                "time_to_profile": 325,
                "time_to_self_buy": 17228431,
                "time_to_first_buy": 17228431,
                "time_to_first_post": 19781798,
                "fee": 456833968,
                "burned": 862220787,
                "tx_count": 72265,
                "transactor_tx_count": 3102
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.me

This method is almost similiar to account.get but used to get current reader state info with extra data to display on your frontend.

#### Request params

You can pass account pubkey or username using reader state in headers.

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>fetch</td><td></td><td>true</td><td>Should contains data that you want include in response. Available: <code>utxos</code>, <code>conversations</code>, <code>creators</code>,<code>daos</code>, <code>notifications</code>. Default is empty list array.</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit lists to this value. Default is 50</td></tr></tbody></table>

#### Response

Return [account structure](structures.md#account) but with extra fields in it related to current reader state.

If `fetch` param passed with non empty array response also includes lists responses of requested structures in same key.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s -H 'X-Reader-Account: diamondhands' --data '[{"method":"account.me"}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "height": 6042,
            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
            "balance": 1202557738544,
            "timestamp": 1615574505,
            "profile": {
                "timestamp": 1615574830,
                "is_hidden": false,
                "height": 6043,
                "username": "diamondhands",
                "description": "💎🙌",
                "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                "reward_points": 0,
                "stake_points": 12500
            },
            "coin": {
                "supply": 164217523869,
                "locked": 4578709213058,
                "watermark": 255810788786,
                "price": 27881976936
            },
            "stat": {
                "last_stat_ts": 1641133448,
                "utxo_count": 5471,
                "holder_count": 3684,
                "holding_count": 2663,
                "follower_count": 23962,
                "following_count": 31,
                "coin_buy_count": 81,
                "coin_buy_value": 8611846815339,
                "coin_sell_count": 2,
                "coin_sell_value": 60683183,
                "coin_gain": -835936510603,
                "sender_connection_count": 943,
                "sender_connection_value": 769238278576,
                "receiver_connection_count": 69975,
                "receiver_connection_value": 131603816393132,
                "sender_seed_count": 1,
                "sender_seed_value": 300000000000,
                "receiver_seed_count": 2,
                "receiver_seed_value": 100000000,
                "sender_coin_count": 1644,
                "sender_coin_value": 835936498462,
                "receiver_coin_count": 9265,
                "receiver_coin_value": 619827916700,
                "reward_coins": 0,
                "reward_value": 0,
                "sender_diamond_count": 6463,
                "sender_diamond_value": 101771508175,
                "receiver_diamond_count": 29474,
                "receiver_diamond_value": 155715519222,
                "post_count": 89,
                "repost_count": 8,
                "quote_count": 34,
                "comment_count": 565,
                "sender_post_like_count": 82,
                "receiver_post_like_count": 70552,
                "nft_count": 0,
                "nft_royalty": 0,
                "nft_coin": 117500000000,
                "nft_mint_count": 2,
                "nft_mint_value": 467500000000,
                "nft_buy_count": 12,
                "nft_buy_value": 51738588404,
                "nft_sell_count": 0,
                "nft_sell_value": 0,
                "nft_gain": 467500000000,
                "sender_nft_bid_count": 0,
                "receiver_nft_bid_count": 152,
                "sender_message_count": 99,
                "recipient_message_count": 2306,
                "sender_conversation_count": 10,
                "recipient_conversation_count": 929,
                "conversation_count": 939,
                "time_to_profile": 325,
                "time_to_self_buy": 17228431,
                "time_to_first_buy": 17228431,
                "time_to_first_post": 19781798,
                "fee": 456833968,
                "burned": 862220787,
                "tx_count": 72265,
                "transactor_tx_count": 3102
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.ping

Send ping notification to server for current reader account that is active and receive pong.

#### Request params

This method has no request params.

#### Response

Just string value of "pong" returned on success

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s -H 'X-Reader-Account: diamondhands' --data '[{"method":"account.ping"}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        "pong"
    ]
]
```
{% endtab %}
{% endtabs %}

### account.list

Get list of accounts sorted by created timestamp (newly created first)

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>has_profile</td><td></td><td>false</td><td>Should we return those who have profiles or just public keys. Default is true.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of [account structures](structures.md#account).

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.list", "params": {"limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 9223372036854775807,
            "list": [
                {
                    "height": 92009,
                    "pubkey": "BC1YLg8hn1FMf6y8Dmws4ic1bWDC4Lk19cYfwvNtSsHWwQfcXbRf7uU",
                    "balance": 23078,
                    "timestamp": 1641136831,
                    "profile": {
                        "timestamp": 1641136831,
                        "is_hidden": false,
                        "height": 92008,
                        "username": "Nibras",
                        "description": "k",
                        "avatar_url": "https://overdeso.com/media/avatar/Z2vWfiPg2gH",
                        "reward_points": 10000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 0,
                        "locked": 0,
                        "watermark": 0,
                        "price": 0
                    },
                    "stat": {
                        "last_stat_ts": 1641136831,
                        "utxo_count": 1,
                        "holder_count": 0,
                        "holding_count": 0,
                        "follower_count": 0,
                        "following_count": 4,
                        "coin_buy_count": 0,
                        "coin_buy_value": 0,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "coin_gain": 0,
                        "sender_connection_count": 0,
                        "sender_connection_value": 0,
                        "receiver_connection_count": 0,
                        "receiver_connection_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "receiver_seed_count": 0,
                        "receiver_seed_value": 0,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "receiver_coin_count": 0,
                        "receiver_coin_value": 0,
                        "reward_coins": 0,
                        "reward_value": 0,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "post_count": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "sender_post_like_count": 0,
                        "receiver_post_like_count": 0,
                        "nft_count": 0,
                        "nft_royalty": 0,
                        "nft_coin": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "nft_gain": 0,
                        "sender_nft_bid_count": 0,
                        "receiver_nft_bid_count": 0,
                        "sender_message_count": 0,
                        "recipient_message_count": 0,
                        "sender_conversation_count": 0,
                        "recipient_conversation_count": 0,
                        "conversation_count": 0,
                        "time_to_profile": 0,
                        "time_to_self_buy": 0,
                        "time_to_first_buy": 0,
                        "time_to_first_post": 0,
                        "fee": 1001922,
                        "burned": 1000000,
                        "tx_count": 7,
                        "transactor_tx_count": 5
                    }
                },
                {
                    "height": 92008,
                    "pubkey": "BC1YLfj2kfHWhTyxgYjQMDuBuyUNmvGDm3F8dj8ecj8wJgq8XWEXP8m",
                    "balance": 10874989,
                    "timestamp": 1641136105,
                    "profile": {
                        "timestamp": 1641136105,
                        "is_hidden": false,
                        "height": 92007,
                        "username": "mprince_net",
                        "description": "",
                        "avatar_url": "https://overdeso.com/media/avatar/YXpVoDhXHay",
                        "reward_points": 10000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 0,
                        "locked": 0,
                        "watermark": 0,
                        "price": 0
                    },
                    "stat": {
                        "last_stat_ts": 1641136105,
                        "utxo_count": 1,
                        "holder_count": 0,
                        "holding_count": 1,
                        "follower_count": 0,
                        "following_count": 2,
                        "coin_buy_count": 0,
                        "coin_buy_value": 0,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "coin_gain": 0,
                        "sender_connection_count": 0,
                        "sender_connection_value": 0,
                        "receiver_connection_count": 0,
                        "receiver_connection_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "receiver_seed_count": 0,
                        "receiver_seed_value": 0,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "receiver_coin_count": 1,
                        "receiver_coin_value": 30818,
                        "reward_coins": 0,
                        "reward_value": 0,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "post_count": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "sender_post_like_count": 0,
                        "receiver_post_like_count": 0,
                        "nft_count": 0,
                        "nft_royalty": 0,
                        "nft_coin": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "nft_gain": 0,
                        "sender_nft_bid_count": 0,
                        "receiver_nft_bid_count": 0,
                        "sender_message_count": 0,
                        "recipient_message_count": 0,
                        "sender_conversation_count": 0,
                        "recipient_conversation_count": 0,
                        "conversation_count": 0,
                        "time_to_profile": 0,
                        "time_to_self_buy": 0,
                        "time_to_first_buy": 0,
                        "time_to_first_post": 0,
                        "fee": 1002758,
                        "burned": 1000000,
                        "tx_count": 6,
                        "transactor_tx_count": 3
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.utxo.list

Find utxo list for account by public key or username

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns utxo list with spendable output and its value. This is can be useful in transaction building.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"account.utxo.list", "params": {"username":"maebeam", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "value": 40241292862,
            "count": 157,
            "list": [
                {
                    "output": [
                        "3JuETruAUtsbwPftVA9MkpZZKVHm7NDD7SZg7YY1cHcxhDP2Fwdatz",
                        3
                    ],
                    "value": 6817500000
                },
                {
                    "output": [
                        "3JuETwqiPvJak4SYXG3PDZ8WKLqLCEz7ai4Dpww6fnpj9RNQ1nMSBM",
                        3
                    ],
                    "value": 6854142038
                },
                {
                    "output": [
                        "3JuESknG9RDp4Wy5e9m6H1gnaszHRaQ1kCUQFcosvTcxax6jk1mU7G",
                        3
                    ],
                    "value": 24509
                },
                {
                    "output": [
                        "3JuEUTafmZRBhWrSfDCgjbqHCxEDNMF3qUMtmJ64hHP6twv6yYAKmT",
                        0
                    ],
                    "value": 22874928216
                },
                {
                    "output": [
                        "3JuEStdjFfCfMcY2DGFAB3THkognpTX8G2uw2aFUSULWafv1v8oXZb",
                        1
                    ],
                    "value": 1385653042
                },
                {
                    "output": [
                        "3JuET9cPq2YkyrQgJCp4a4ciKr993uqPa2d1c2KR6qeDjrJtDoc8E6",
                        0
                    ],
                    "value": 5000000
                },
                {
                    "output": [
                        "3JuETMWRoKb6gmxiKmnwQb2JhXAgAM8bqo3Hz8G766forpAKgjGubs",
                        0
                    ],
                    "value": 5000000
                },
                {
                    "output": [
                        "3JuEUChT5QiL4p8A7fXh2w8pftE9X3xEzcccnX9DEXSrrj9trocHY3",
                        0
                    ],
                    "value": 5000000
                },
                {
                    "output": [
                        "3JuEUDynBzgU1P68Px33snwgSnLqDFYiquCpXQ9f9vxSzTJmA7zgRT",
                        0
                    ],
                    "value": 50000000
                },
                {
                    "output": [
                        "3JuET7k1wWtYetx9JdjQU3EjNvj4xtG8EiqUrK1M8qqdwHREkNM733",
                        0
                    ],
                    "value": 5000000
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.follow.get

Get information if one account follows another one

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>following_pubkey</td><td></td><td>true</td><td>Following username</td></tr><tr><td>following_pubkey</td><td></td><td>true</td><td>Following public key of account</td></tr></tbody></table>

#### Resopnse

This method returns just boolean information if one accounts follow another one.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.follow.get", "params": {"username":"donhardman", "following_username":"diamondhands"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        true
    ]
]
```
{% endtab %}
{% endtabs %}

### account.follow.list

Find accounts which the person following or which following that person.

The method requires one of **username** or **pubkey** to be passed in request body.

#### Request params <a href="#request-params" id="request-params"></a>

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be following or follower.</td></tr><tr><td>expand</td><td></td><td>false</td><td>If set to true we expand account info instead of just pubkey and username returned in item. Default is false.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returnes list of follower or following accounts.

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.follow.list", "params": {"account":"diamondhands", "type": "following", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 31,
            "list": [
                {
                    "pubkey": "BC1YLi6LpXTemAG8T9ptyWAkMywrjynwZcKjB5DkDXxrsG5kgAwAqxq",
                    "username": "maebeam",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLiU9Wpk8c7pVx7GCu8fae6AQhdUrGYcWc1Wz9V56HbCi7RPr887",
                    "username": "balajis",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLi3P5VRwVaABUCrQQHEEUoQGoAUpcS272Rb16MDH1Uy8Kg9q3sX",
                    "username": "helenowen",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLhqEhWvNnwW9TBqXURFqwkdpUYKrMVgTHQzopF5rRBDcD1LLSUp",
                    "username": "artz",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLj4iUraQabhUBT8kS1gCieXhD1GGXeFCcU3qM3MGgf7GwBJ9Va7",
                    "username": "craig",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLgHUYA2phkKYS6LdLLhkfGW7XkKX2D1Ktp5HVT8TpNGcah9KexY",
                    "username": "dharmann",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLjERk6o1wsh8NMhKKebBsyzjBVGSMwMy9e45VgZUmwWaTWWZcRT",
                    "username": "Drseuss",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLhoXx7AxSDdcz8mhFKmcP5jzA2Z8tXDjUTsttGe7rE7sK3Ures7",
                    "username": "BennyBlanco",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLg5xgL7PAToY7dNrxqRmtAarJvBBZKJTkreuv2eLvCppf58Pwn9",
                    "username": "Doodles",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                },
                {
                    "pubkey": "BC1YLiQqFd4ro1jw3XTZ4zxMjEQka7NXy4aTc8Km1oeDHwjBn2kXrDy",
                    "username": "rrhoover",
                    "state": {
                        "is_following": false,
                        "is_follower": false
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.highlight.list

Get highlighted accounts to show.

#### Request params

This method does not require any params.

#### Response

Returns 5 accounts that should be higlighted.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.highlight.list"}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "height": 104918,
                "pubkey": "BC1YLhvBTGzjCDrPbHV1EAoFsygMgm2ZrtxefyN1sfqGGY1BbJoYDvv",
                "balance": 116118,
                "timestamp": 1645088687,
                "profile": {
                    "timestamp": 1645088906,
                    "is_hidden": false,
                    "height": 104918,
                    "username": "Rafaaa",
                    "description": "Marketing Digital 🎯📈🚀",
                    "avatar_url": "http://media.overdeso.lo/avatar/iQ5b6GXQxsv",
                    "reward_points": 10000,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 0,
                    "locked": 0,
                    "watermark": 0,
                    "price": 0
                },
                "dao": null,
                "stat": {
                    "last_stat_ts": 1645092407,
                    "utxo_count": 3,
                    "level_points": 148,
                    "holder_count": 0,
                    "holding_count": 1,
                    "follower_count": 3,
                    "following_count": 6,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "coin_gain": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 1,
                    "receiver_coin_value": 30150,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "dao": 0,
                    "dao_mint_count": 0,
                    "dao_burn_count": 0,
                    "dao_disable_count": 0,
                    "dao_restrict_count": 0,
                    "dao_holder_count": 0,
                    "dao_holding_count": 0,
                    "sender_dao_count": 0,
                    "receiver_dao_count": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 2,
                    "receiver_diamond_value": 100000,
                    "post_count": 3,
                    "repost_count": 1,
                    "quote_count": 0,
                    "comment_count": 0,
                    "sender_post_like_count": 8,
                    "receiver_post_like_count": 6,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0,
                    "sender_nft_bid_count": 0,
                    "receiver_nft_bid_count": 0,
                    "sender_message_count": 0,
                    "recipient_message_count": 0,
                    "sender_conversation_count": 0,
                    "recipient_conversation_count": 0,
                    "conversation_count": 0,
                    "conversation_group_count": 0,
                    "time_to_profile": 219,
                    "time_to_self_buy": 0,
                    "time_to_first_buy": 0,
                    "time_to_first_post": 4704,
                    "fee": 8882,
                    "burned": 1000000,
                    "tx_count": 29,
                    "transactor_tx_time": 1645093391,
                    "transactor_tx_height": 104935,
                    "transactor_tx_count": 21,
                    "tx_23_count": 0,
                    "tx_26_count": 0,
                    "sender_seed_count": 0,
                    "sender_seed_value": 0,
                    "receiver_seed_count": 0,
                    "receiver_seed_value": 0,
                    "sender_connection_count": 0,
                    "sender_connection_value": 0,
                    "receiver_connection_count": 0,
                    "receiver_connection_value": 0
                }
            },
            {
                "height": 104917,
                "pubkey": "BC1YLj9ZAjVWgQYagRSkVTDHGDCbDhR2j1boquCFNERAYpSoxsqBMJd",
                "balance": 69193,
                "timestamp": 1645088118,
                "profile": {
                    "timestamp": 1645088180,
                    "is_hidden": false,
                    "height": 104916,
                    "username": "SeruyWorld",
                    "description": "",
                    "avatar_url": "http://media.overdeso.lo/avatar/gtmXtVdzUvg",
                    "reward_points": 10000,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 0,
                    "locked": 0,
                    "watermark": 0,
                    "price": 0
                },
                "dao": null,
                "stat": {
                    "last_stat_ts": 1645088118,
                    "utxo_count": 2,
                    "level_points": 176,
                    "holder_count": 0,
                    "holding_count": 1,
                    "follower_count": 0,
                    "following_count": 0,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "coin_gain": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 1,
                    "receiver_coin_value": 30150,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "dao": 0,
                    "dao_mint_count": 0,
                    "dao_burn_count": 0,
                    "dao_disable_count": 0,
                    "dao_restrict_count": 0,
                    "dao_holder_count": 0,
                    "dao_holding_count": 0,
                    "sender_dao_count": 0,
                    "receiver_dao_count": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 1,
                    "receiver_diamond_value": 50000,
                    "post_count": 6,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "sender_post_like_count": 6,
                    "receiver_post_like_count": 6,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0,
                    "sender_nft_bid_count": 0,
                    "receiver_nft_bid_count": 0,
                    "sender_message_count": 0,
                    "recipient_message_count": 0,
                    "sender_conversation_count": 0,
                    "recipient_conversation_count": 0,
                    "conversation_count": 0,
                    "conversation_group_count": 0,
                    "time_to_profile": 62,
                    "time_to_self_buy": 0,
                    "time_to_first_buy": 0,
                    "time_to_first_post": 900,
                    "fee": 5807,
                    "burned": 1000000,
                    "tx_count": 17,
                    "transactor_tx_time": 1645089119,
                    "transactor_tx_height": 104919,
                    "transactor_tx_count": 13,
                    "tx_23_count": 0,
                    "tx_26_count": 0,
                    "sender_seed_count": 0,
                    "sender_seed_value": 0,
                    "receiver_seed_count": 0,
                    "receiver_seed_value": 0,
                    "sender_connection_count": 0,
                    "sender_connection_value": 0,
                    "receiver_connection_count": 0,
                    "receiver_connection_value": 0
                }
            },
            {
                "height": null,
                "pubkey": "BC1YLgTJoi9virz5Ba4s2TjvcTp9aUMXZYyJC2HyePSGXNAAMYshPDa",
                "balance": 0,
                "timestamp": 1645093742,
                "profile": {
                    "timestamp": 1645093808,
                    "is_hidden": false,
                    "height": 104935,
                    "username": "Saimks51",
                    "description": "",
                    "avatar_url": "http://media.overdeso.lo/avatar/RLbBEmztegC",
                    "reward_points": 10000,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 0,
                    "locked": 0,
                    "watermark": 0,
                    "price": 0
                },
                "dao": null,
                "stat": {
                    "last_stat_ts": 1645093742,
                    "utxo_count": 0,
                    "level_points": 40,
                    "holder_count": 0,
                    "holding_count": 1,
                    "follower_count": 1,
                    "following_count": 5,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "coin_gain": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 1,
                    "receiver_coin_value": 30150,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "dao": 0,
                    "dao_mint_count": 0,
                    "dao_burn_count": 0,
                    "dao_disable_count": 0,
                    "dao_restrict_count": 0,
                    "dao_holder_count": 0,
                    "dao_holding_count": 0,
                    "sender_dao_count": 0,
                    "receiver_dao_count": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "post_count": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "sender_post_like_count": 0,
                    "receiver_post_like_count": 0,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0,
                    "sender_nft_bid_count": 0,
                    "receiver_nft_bid_count": 0,
                    "sender_message_count": 0,
                    "recipient_message_count": 0,
                    "sender_conversation_count": 0,
                    "recipient_conversation_count": 0,
                    "conversation_count": 0,
                    "conversation_group_count": 0,
                    "time_to_profile": 66,
                    "time_to_self_buy": 0,
                    "time_to_first_buy": 0,
                    "time_to_first_post": 0,
                    "fee": 2335,
                    "burned": 1000000,
                    "tx_count": 11,
                    "transactor_tx_time": 1645093989,
                    "transactor_tx_height": 0,
                    "transactor_tx_count": 7,
                    "tx_23_count": 0,
                    "tx_26_count": 0,
                    "sender_seed_count": 0,
                    "sender_seed_value": 0,
                    "receiver_seed_count": 0,
                    "receiver_seed_value": 0,
                    "sender_connection_count": 0,
                    "sender_connection_value": 0,
                    "receiver_connection_count": 0,
                    "receiver_connection_value": 0
                }
            },
            {
                "height": 104935,
                "pubkey": "BC1YLha7kWTwUz5y3fEcASbA5dNhJS8vgYHsZJDP2CmxosXsyFdjEEU",
                "balance": 22856,
                "timestamp": 1645093497,
                "profile": {
                    "timestamp": 1645093640,
                    "is_hidden": false,
                    "height": 104935,
                    "username": "BAzenga",
                    "description": "",
                    "avatar_url": "http://media.overdeso.lo/avatar/RAtWAppaE6p",
                    "reward_points": 10000,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 0,
                    "locked": 0,
                    "watermark": 0,
                    "price": 0
                },
                "dao": null,
                "stat": {
                    "last_stat_ts": 1645093497,
                    "utxo_count": 1,
                    "level_points": 43,
                    "holder_count": 0,
                    "holding_count": 1,
                    "follower_count": 1,
                    "following_count": 5,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "coin_gain": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 1,
                    "receiver_coin_value": 30150,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "dao": 0,
                    "dao_mint_count": 0,
                    "dao_burn_count": 0,
                    "dao_disable_count": 0,
                    "dao_restrict_count": 0,
                    "dao_holder_count": 0,
                    "dao_holding_count": 0,
                    "sender_dao_count": 0,
                    "receiver_dao_count": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "post_count": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "sender_post_like_count": 0,
                    "receiver_post_like_count": 0,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0,
                    "sender_nft_bid_count": 0,
                    "receiver_nft_bid_count": 0,
                    "sender_message_count": 0,
                    "recipient_message_count": 0,
                    "sender_conversation_count": 0,
                    "recipient_conversation_count": 0,
                    "conversation_count": 0,
                    "conversation_group_count": 0,
                    "time_to_profile": 143,
                    "time_to_self_buy": 0,
                    "time_to_first_buy": 0,
                    "time_to_first_post": 0,
                    "fee": 2144,
                    "burned": 1000000,
                    "tx_count": 10,
                    "transactor_tx_time": 1645093652,
                    "transactor_tx_height": 0,
                    "transactor_tx_count": 6,
                    "tx_23_count": 0,
                    "tx_26_count": 0,
                    "sender_seed_count": 0,
                    "sender_seed_value": 0,
                    "receiver_seed_count": 0,
                    "receiver_seed_value": 0,
                    "sender_connection_count": 0,
                    "sender_connection_value": 0,
                    "receiver_connection_count": 0,
                    "receiver_connection_value": 0
                }
            },
            {
                "height": 104935,
                "pubkey": "BC1YLgSC9R8BAfUxUBGFjqNCm4MVNeVY9GdzgUMuUQDXdDywbjzW4yZ",
                "balance": 22795,
                "timestamp": 1645093272,
                "profile": {
                    "timestamp": 1645093652,
                    "is_hidden": false,
                    "height": 104935,
                    "username": "Precious89",
                    "description": "",
                    "avatar_url": "http://media.overdeso.lo/avatar/R1Bq2MEUbu6",
                    "reward_points": 10000,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 0,
                    "locked": 0,
                    "watermark": 0,
                    "price": 0
                },
                "dao": null,
                "stat": {
                    "last_stat_ts": 1645093272,
                    "utxo_count": 1,
                    "level_points": 56,
                    "holder_count": 0,
                    "holding_count": 0,
                    "follower_count": 0,
                    "following_count": 0,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "coin_gain": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "dao": 0,
                    "dao_mint_count": 0,
                    "dao_burn_count": 0,
                    "dao_disable_count": 0,
                    "dao_restrict_count": 0,
                    "dao_holder_count": 0,
                    "dao_holding_count": 0,
                    "sender_dao_count": 0,
                    "receiver_dao_count": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "post_count": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "sender_post_like_count": 0,
                    "receiver_post_like_count": 0,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0,
                    "sender_nft_bid_count": 0,
                    "receiver_nft_bid_count": 0,
                    "sender_message_count": 0,
                    "recipient_message_count": 0,
                    "sender_conversation_count": 0,
                    "recipient_conversation_count": 0,
                    "conversation_count": 0,
                    "conversation_group_count": 0,
                    "time_to_profile": 380,
                    "time_to_self_buy": 0,
                    "time_to_first_buy": 0,
                    "time_to_first_post": 0,
                    "fee": 2205,
                    "burned": 1000000,
                    "tx_count": 3,
                    "transactor_tx_time": 1645093652,
                    "transactor_tx_height": 0,
                    "transactor_tx_count": 1,
                    "tx_23_count": 0,
                    "tx_26_count": 0,
                    "sender_seed_count": 0,
                    "sender_seed_value": 0,
                    "receiver_seed_count": 0,
                    "receiver_seed_value": 0,
                    "sender_connection_count": 0,
                    "sender_connection_value": 0,
                    "receiver_connection_count": 0,
                    "receiver_connection_value": 0
                }
            },
            {
                "height": 104933,
                "pubkey": "BC1YLiBNpq5xZ9XSEA7iiPTRxdLKSV3M9Biey23tsUN4pkSPowLWNsv",
                "balance": 22858,
                "timestamp": 1645092916,
                "profile": {
                    "timestamp": 1645093277,
                    "is_hidden": false,
                    "height": 104934,
                    "username": "Wac17",
                    "description": "",
                    "avatar_url": "http://media.overdeso.lo/avatar/QfnV9K9U8Qt",
                    "reward_points": 10000,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 0,
                    "locked": 0,
                    "watermark": 0,
                    "price": 0
                },
                "dao": null,
                "stat": {
                    "last_stat_ts": 1645092916,
                    "utxo_count": 1,
                    "level_points": 86,
                    "holder_count": 0,
                    "holding_count": 1,
                    "follower_count": 1,
                    "following_count": 5,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "coin_gain": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 1,
                    "receiver_coin_value": 30150,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "dao": 0,
                    "dao_mint_count": 0,
                    "dao_burn_count": 0,
                    "dao_disable_count": 0,
                    "dao_restrict_count": 0,
                    "dao_holder_count": 0,
                    "dao_holding_count": 0,
                    "sender_dao_count": 0,
                    "receiver_dao_count": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "post_count": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "sender_post_like_count": 0,
                    "receiver_post_like_count": 0,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0,
                    "sender_nft_bid_count": 0,
                    "receiver_nft_bid_count": 0,
                    "sender_message_count": 0,
                    "recipient_message_count": 0,
                    "sender_conversation_count": 0,
                    "recipient_conversation_count": 0,
                    "conversation_count": 0,
                    "conversation_group_count": 0,
                    "time_to_profile": 361,
                    "time_to_self_buy": 0,
                    "time_to_first_buy": 0,
                    "time_to_first_post": 0,
                    "fee": 2142,
                    "burned": 1000000,
                    "tx_count": 10,
                    "transactor_tx_time": 1645093493,
                    "transactor_tx_height": 104935,
                    "transactor_tx_count": 6,
                    "tx_23_count": 0,
                    "tx_26_count": 0,
                    "sender_seed_count": 0,
                    "sender_seed_value": 0,
                    "receiver_seed_count": 0,
                    "receiver_seed_value": 0,
                    "sender_connection_count": 0,
                    "sender_connection_value": 0,
                    "receiver_connection_count": 0,
                    "receiver_connection_value": 0
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### account.seed.list

Get list of seeders for the account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be sender or receiver. Default: receiver.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start default is 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch for the request. Default is 10.</td></tr></tbody></table>

#### Response

Reposponse contains 2 keys: **count** and **list**.&#x20;

**list** contains simple list of account information that has 2 keys: **pubkey** and **username**.

**count** – total count of transactions that related to this account.

**value** – total nanos seeded for all accounts or from all accounts depending on **type** param.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.seed.list", "params": {"username":"diamondhands", "type": "receiver", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "value": 50000000,
            "count": 1,
            "list": [
                {
                    "pubkey": "BC1YLhNsBQppF1Xn2tqRPUv7BiB6Ln1cJPHVyBEXKN92tVaEwnkWLLD",
                    "username": "merlin",
                    "value": 50000000
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.connection.list

Get connections for account pubkey or username.

#### Request params



<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be sender or receiver. Default: receiver.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start default is 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch for the request. Default is 10.</td></tr></tbody></table>

#### Response

TODO

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.connection.list", "params": {"username":"diamondhands", "type": "receiver", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "value": 0,
            "count": 74564,
            "list": [
                {
                    "pubkey": "BC1YLiwCtwj9py5ekJFeXaxLmC8Z78qrBPiegZVqH9fRXh5hv7HFQpz",
                    "username": "WhaleSharkIsSCAMMER",
                    "count": 143,
                    "value": 24945535425461
                },
                {
                    "pubkey": "BC1YLgT36phrdWaCLHV5mm65c1UgJJuHFcYcPEz1tK5mrtDmLBUf8ak",
                    "username": "Peps",
                    "count": 47,
                    "value": 11180482151718
                }
            ]
        }
    ]

```
{% endtab %}
{% endtabs %}

### account.trade.list

Get information about creator coin for account as investor or as creator.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be investor or creator. First one for fetching information for account as investor and second one as creator.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of coins and account infos.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.trade.list", "params": {"account":"diamondhands", "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 37,
            "list": [
                {
                    "operation": "transfer",
                    "gain": -52429,
                    "value": 52429,
                    "coins": 630,
                    "id": "3JuEUW6YLkHTd5skecgvonQCxkwktSgd5FTsJoy7bxT61qNQdsYj9J",
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 23264863206,
                        "timestamp": 1615574505,
                        "profile": {
                            "timestamp": 1615574830,
                            "is_hidden": false,
                            "height": 6043,
                            "username": "diamondhands",
                            "description": "💎🙌",
                            "avatar_url": "http://media.overdeso.lo/avatar/Xs8Q7X2MDLy",
                            "reward_points": 0,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 166563551584,
                            "locked": 4621048828164,
                            "watermark": 255810788786,
                            "price": 27743457582
                        }
                    },
                    "receiver": {
                        "height": 25784,
                        "pubkey": "BC1YLgJErwUC6xUmCy3vcPhp3E8DAjR9WqMpDYqBqPxoNQs88huJJEp",
                        "balance": 9237697739,
                        "timestamp": 1621410619,
                        "profile": {
                            "timestamp": 1621410619,
                            "is_hidden": false,
                            "height": 25783,
                            "username": "virenderkhanna",
                            "description": "Curiosity got me here ! ",
                            "avatar_url": "http://media.overdeso.lo/avatar/Qfu5d95rfkh",
                            "reward_points": 10000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 500000000,
                            "locked": 125000,
                            "watermark": 11767956861,
                            "price": 250000
                        }
                    }
                },
                {
                    "operation": "transfer",
                    "gain": -5249395,
                    "value": 5249395,
                    "coins": 63077,
                    "id": "3JuETgXBHeRwkfYBRLQKxi4qjKZ4j7oJ36pgnEMNKDHVgvJpuX1CuB",
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 23264863206,
                        "timestamp": 1615574505,
                        "profile": {
                            "timestamp": 1615574830,
                            "is_hidden": false,
                            "height": 6043,
                            "username": "diamondhands",
                            "description": "💎🙌",
                            "avatar_url": "http://media.overdeso.lo/avatar/Xs8Q7X2MDLy",
                            "reward_points": 0,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 166563551584,
                            "locked": 4621048828164,
                            "watermark": 255810788786,
                            "price": 27743457582
                        }
                    },
                    "receiver": {
                        "height": 20769,
                        "pubkey": "BC1YLgvhbxCR181wxuEAzm8rR8uVfdYnuBQXtTchJSzJmZGG2mGigJL",
                        "balance": 20978227,
                        "timestamp": 1620034162,
                        "profile": {
                            "timestamp": 1620036256,
                            "is_hidden": false,
                            "height": 20778,
                            "username": "AndrewVanDuivenbode",
                            "description": "Scottish Software Developer\nCreative Transmissions & TransitQuote Founder \nDoing: JavaScript/Database Development, PHP/ Laravel/WordPress\nInterests: Virtual Worlds, Space, Tech\n\n",
                            "avatar_url": "http://media.overdeso.lo/avatar/XXef96doQV3",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 4100319729,
                            "locked": 68937208,
                            "watermark": 5086152504,
                            "price": 16812642
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

### account.notification.list

Get account notifications for username or public key.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>type_id</td><td></td><td>false</td><td>Filter only wanter notification type</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Type ID map

|          |   |
| -------- | - |
| Transfer | 0 |
| Follow   | 1 |
| Like     | 2 |
| Comment  | 3 |
| Coin     | 4 |
| Diamond  | 5 |
| Mention  | 6 |
| Repost   | 7 |
| DAO      | 8 |

#### Response

The method returns notifications related to requested accounts in choronological order (new first)

**count** – how many rows total in your request.

**list** – list of account notification structure.

Notification are groupped by short time period in lists.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.notification.list", "params": {"account":"krassenstein", "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 5,
            "list": [
                {
                    "type_id": 2,
                    "data": [
                        {
                            "transactor": {
                                "height": 68438,
                                "pubkey": "BC1YLic8jUPXsVmFiEASjeJyRdkxMZGEbRHToZcoGx8zw3syc1K9A2Q",
                                "balance": 2656076290,
                                "timestamp": 1634039774,
                                "profile": {
                                    "timestamp": 1634861319,
                                    "is_hidden": false,
                                    "height": 71201,
                                    "username": "stockler",
                                    "description": "Just a dev trying drop anxiety when going to sleep and maintain my sanity when wake up.\n\nhttps://github.com/stockler\n\nTwitter: https://twitter.com/RafaelStockler1",
                                    "avatar_url": "http://media.overdeso.lo/avatar/UgaRoyPjrNU",
                                    "reward_points": 314,
                                    "stake_points": 12500
                                },
                                "coin": {
                                    "supply": 9355542024,
                                    "locked": 837265937,
                                    "watermark": 10783319273,
                                    "price": 89494113
                                },
                                "stat": {
                                    "last_stat_ts": 1642431173,
                                    "utxo_count": 251,
                                    "level_points": 9,
                                    "holder_count": 13,
                                    "holding_count": 95,
                                    "follower_count": 280,
                                    "following_count": 706,
                                    "coin_buy_count": 144,
                                    "coin_buy_value": 1055495471,
                                    "coin_sell_count": 42,
                                    "coin_sell_value": 401816847,
                                    "coin_gain": 43077853,
                                    "sender_coin_count": 0,
                                    "sender_coin_value": 0,
                                    "receiver_coin_count": 69,
                                    "receiver_coin_value": 37086709,
                                    "reward_coins": 0,
                                    "reward_value": 194104415,
                                    "sender_diamond_count": 61,
                                    "sender_diamond_value": 3050000,
                                    "receiver_diamond_count": 281,
                                    "receiver_diamond_value": 141850000,
                                    "post_count": 44,
                                    "repost_count": 236,
                                    "quote_count": 106,
                                    "comment_count": 258,
                                    "sender_post_like_count": 3180,
                                    "receiver_post_like_count": 867,
                                    "nft_count": 0,
                                    "nft_royalty": 2529411,
                                    "nft_coin": 2529411,
                                    "nft_mint_count": 1,
                                    "nft_mint_value": 20235295,
                                    "nft_buy_count": 1,
                                    "nft_buy_value": 121536,
                                    "nft_sell_count": 0,
                                    "nft_sell_value": 0,
                                    "nft_gain": 20235295,
                                    "sender_nft_bid_count": 1,
                                    "receiver_nft_bid_count": 3,
                                    "sender_message_count": 59,
                                    "recipient_message_count": 35,
                                    "sender_conversation_count": 8,
                                    "recipient_conversation_count": 4,
                                    "conversation_count": 12,
                                    "time_to_profile": 821545,
                                    "time_to_self_buy": 3165164,
                                    "time_to_first_buy": 8300964,
                                    "time_to_first_post": 8393254,
                                    "fee": 1210419,
                                    "burned": 1285832,
                                    "tx_count": 5732,
                                    "transactor_tx_time": 1642433098,
                                    "transactor_tx_height": 96250,
                                    "transactor_tx_count": 4962,
                                    "sender_seed_count": 0,
                                    "sender_seed_value": 0,
                                    "receiver_seed_count": 1,
                                    "receiver_seed_value": 41716666,
                                    "sender_connection_count": 4475,
                                    "sender_connection_value": 1046891878,
                                    "receiver_connection_count": 1567,
                                    "receiver_connection_value": 4045893431
                                }
                            },
                            "post": {
                                "depth": 0,
                                "is_quoted": false,
                                "text": "Deso Day 296\n- Tornados have us a bit flustered.\n- New Node stats, thanks to @OpenProsper, show how well @Desocialworld @Tunel and @Cloutfeed are doing.\n- @HazRodriguez explains @Tunel's success\n- BusinessInsider Publishes article by @Tobyhazelwood about Deso and NFTs\n- Also mentioned in this video: @tijn @NFTz @whatsmygas @whoamI @Nader\n\nSponsored by: @NFTtech\n\nPosted via @cloutfeed",
                                "lang": "en",
                                "has_media": true,
                                "has_image": false,
                                "has_video": true,
                                "media": {
                                    "embed_video_url": "https://www.youtube.com/embed/Oo0eAOXq0NY"
                                },
                                "is_hidden": false,
                                "is_nft": false,
                                "submitted_at": 1642363813,
                                "nft": null,
                                "stat": {
                                    "last_stat_ts": 1642432541,
                                    "like_count": 45,
                                    "diamond_count": 36,
                                    "diamond_value": 111500000,
                                    "repost_count": 12,
                                    "quote_count": 4,
                                    "comment_count": 13,
                                    "nft_bid_count": 0,
                                    "nft_trade_count": 0,
                                    "nft_burned_count": 0
                                }
                            },
                            "is_unlike": false
                        }
                    ],
                    "timestamp": 1642433099
                },
                {
                    "type_id": 4,
                    "data": [
                        {
                            "transactor": {
                                "height": 95349,
                                "pubkey": "BC1YLinyu9KkuQaywPJhCBYnGrpPeeA4fVQH8sPUw1Yf1ZZEYj9jyTF",
                                "balance": 1287505917,
                                "timestamp": 1642164864,
                                "profile": {
                                    "timestamp": 1642164864,
                                    "is_hidden": false,
                                    "height": 95348,
                                    "username": "Bemyportraitmuse",
                                    "description": "Professional photographer/mentor/NFT artist\n\nPortfolio/instagram @bemyportraitmuse\n\nThank you for visiting my page, I'll be glad to meet you!",
                                    "avatar_url": "http://media.overdeso.lo/avatar/VMRKS1UZ2U4",
                                    "reward_points": 2000,
                                    "stake_points": 12500
                                },
                                "coin": {
                                    "supply": 6853227509,
                                    "locked": 321873823,
                                    "watermark": 6853227509,
                                    "price": 46966749
                                },
                                "stat": {
                                    "last_stat_ts": 1642431613,
                                    "utxo_count": 197,
                                    "level_points": 348,
                                    "holder_count": 7,
                                    "holding_count": 9,
                                    "follower_count": 22,
                                    "following_count": 30,
                                    "coin_buy_count": 9,
                                    "coin_buy_value": 348467057,
                                    "coin_sell_count": 0,
                                    "coin_sell_value": 0,
                                    "coin_gain": -113606455,
                                    "sender_coin_count": 1,
                                    "sender_coin_value": 113606455,
                                    "receiver_coin_count": 4,
                                    "receiver_coin_value": 112287,
                                    "reward_coins": 0,
                                    "reward_value": 44324332,
                                    "sender_diamond_count": 7,
                                    "sender_diamond_value": 750000,
                                    "receiver_diamond_count": 38,
                                    "receiver_diamond_value": 3100000,
                                    "post_count": 6,
                                    "repost_count": 1,
                                    "quote_count": 4,
                                    "comment_count": 15,
                                    "sender_post_like_count": 59,
                                    "receiver_post_like_count": 72,
                                    "nft_count": 0,
                                    "nft_royalty": 0,
                                    "nft_coin": 0,
                                    "nft_mint_count": 0,
                                    "nft_mint_value": 0,
                                    "nft_buy_count": 0,
                                    "nft_buy_value": 0,
                                    "nft_sell_count": 0,
                                    "nft_sell_value": 0,
                                    "nft_gain": 0,
                                    "sender_nft_bid_count": 0,
                                    "receiver_nft_bid_count": 0,
                                    "sender_message_count": 0,
                                    "recipient_message_count": 0,
                                    "sender_conversation_count": 0,
                                    "recipient_conversation_count": 0,
                                    "conversation_count": 0,
                                    "time_to_profile": 0,
                                    "time_to_self_buy": 79901,
                                    "time_to_first_buy": 268199,
                                    "time_to_first_post": 263263,
                                    "fee": 49974,
                                    "burned": 1084849,
                                    "tx_count": 250,
                                    "transactor_tx_time": 1642433063,
                                    "transactor_tx_height": 96250,
                                    "transactor_tx_count": 145,
                                    "sender_seed_count": 0,
                                    "sender_seed_value": 0,
                                    "receiver_seed_count": 0,
                                    "receiver_seed_value": 0,
                                    "sender_connection_count": 89,
                                    "sender_connection_value": 141824571,
                                    "receiver_connection_count": 177,
                                    "receiver_connection_value": 622910197
                                }
                            },
                            "coin": {
                                "operation": "buy",
                                "gain": 0,
                                "value": 14206563,
                                "coins": 580343
                            }
                        }
                    ],
                    "timestamp": 1642433091
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.stat.list

Get account historical stats for username or public key.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>period</td><td></td><td>false</td><td>Aggregation period. One of: hour, day, month. Default is hour</td></tr><tr><td>start_at</td><td></td><td>false</td><td>Timestamp to start our lookup. Default is 1610948544 that is genesis block timestamp. That means we fetch from first stat record.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns statistic related data in chronological order (low to high).

**count** – how many rows total in your request.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.stat.list", "params": {"account":"diamondhands", "period": "hour", "start_at": 1616174306, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 6934,
            "list": [
                {
                    "ts": 1616173200,
                    "holder_count": 0,
                    "holding_count": 0,
                    "follower_count": 0,
                    "following_count": 0,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "tx_count": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "post_count": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0
                },
                {
                    "ts": 1616176800,
                    "holder_count": 0,
                    "holding_count": 0,
                    "follower_count": 257,
                    "following_count": 0,
                    "coin_buy_count": 0,
                    "coin_buy_value": 0,
                    "coin_sell_count": 0,
                    "coin_sell_value": 0,
                    "tx_count": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "post_count": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0,
                    "nft_count": 0,
                    "nft_royalty": 0,
                    "nft_coin": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "nft_gain": 0
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.rank.list

Get account rankings sorted in high to low order by requested type stat key.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>What type of rankings we need to get. Default is <code>locked</code>. Allowed values: <code>locked</code>, <code>balance</code>, <code>reward_value</code>, <code>coin_gain</code>, <code>follower_count</code>, <code>nft_coin</code>, <code>nft_royalty</code>, <code>nft_gain</code>, <code>sender_diamond_value</code>, <code>receiver_diamond_value</code>, <code>post_count</code>, <code>comment_count</code>, <code>level_points</code></td></tr><tr><td>sorting</td><td></td><td>false</td><td>One of: value or change.<br><code>value</code> – we sort by value for all time.<br><code>change</code> – we sort by daily change on request value rank.</td></tr><tr><td>range</td><td></td><td>false</td><td>Represents list with min max values or default []. First index - min, second one - max. In case you pass it you will get narrowed ranking in this range</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of accounts with rank field.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.rank.list", "params": {"type":"locked", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 278265,
            "list": [
                {
                    "height": 2,
                    "pubkey": "BC1YLiFNARSWF6qtXM5acrS7q8VWPeeS2gycVBtqLALkE4c1V3kx4US",
                    "balance": 1600055637,
                    "timestamp": 1614598233,
                    "profile": {
                        "timestamp": 1614598233,
                        "is_hidden": false,
                        "height": 1,
                        "username": "elonmusk",
                        "description": "",
                        "avatar_url": "https://overdeso.com/media/avatar/hu6ANhCXLUy",
                        "reward_points": 0,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 303850285701,
                        "locked": 28053023771200,
                        "watermark": 453559032340,
                        "price": 92325151863
                    },
                    "stat": {
                        "last_stat_ts": 1641218186,
                        "utxo_count": 44,
                        "holder_count": 9538,
                        "holding_count": 108,
                        "follower_count": 24171,
                        "following_count": 0,
                        "coin_buy_count": 2,
                        "coin_buy_value": 79595351183,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "coin_gain": 0,
                        "sender_connection_count": 11,
                        "sender_connection_value": 20000,
                        "receiver_connection_count": 54180,
                        "receiver_connection_value": 389288119986612,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "receiver_seed_count": 0,
                        "receiver_seed_value": 0,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "receiver_coin_count": 133,
                        "receiver_coin_value": 21579865722,
                        "reward_coins": 0,
                        "reward_value": 0,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "post_count": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "sender_post_like_count": 0,
                        "receiver_post_like_count": 0,
                        "nft_count": 0,
                        "nft_royalty": 0,
                        "nft_coin": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "nft_gain": 0,
                        "sender_nft_bid_count": 0,
                        "receiver_nft_bid_count": 0,
                        "sender_message_count": 0,
                        "recipient_message_count": 222,
                        "sender_conversation_count": 0,
                        "recipient_conversation_count": 133,
                        "conversation_count": 133,
                        "time_to_profile": 0,
                        "time_to_self_buy": 861554,
                        "time_to_first_buy": 861554,
                        "time_to_first_post": 0,
                        "fee": 3708,
                        "burned": 8959536,
                        "tx_count": 54227,
                        "transactor_tx_count": 3
                    },
                    "rank": {
                        "position": 1,
                        "change": 0
                    }
                },
                {
                    "height": 5769,
                    "pubkey": "BC1YLgVNKrgTYt1QaeTCW46KMRfCNEAEKrgWdEDUKSQsd42JfQMNncs",
                    "balance": 35611736354,
                    "timestamp": 1615511001,
                    "profile": {
                        "timestamp": 1615529337,
                        "is_hidden": false,
                        "height": 5839,
                        "username": "naval",
                        "description": "",
                        "avatar_url": "https://overdeso.com/media/avatar/bNpKnvmWC57",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 255655972940,
                        "locked": 16709694719061,
                        "watermark": 353048906645,
                        "price": 65360079511
                    },
                    "stat": {
                        "last_stat_ts": 1641218186,
                        "utxo_count": 638,
                        "holder_count": 1386,
                        "holding_count": 33,
                        "follower_count": 8290,
                        "following_count": 0,
                        "coin_buy_count": 1,
                        "coin_buy_value": 95145650200,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "coin_gain": 0,
                        "sender_connection_count": 3,
                        "sender_connection_value": 100000000,
                        "receiver_connection_count": 13412,
                        "receiver_connection_value": 88165065194882,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "receiver_seed_count": 1,
                        "receiver_seed_value": 94822628903,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "receiver_coin_count": 35,
                        "receiver_coin_value": 26613315925,
                        "reward_coins": 30793004148,
                        "reward_value": 5706170956481,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "post_count": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "sender_post_like_count": 0,
                        "receiver_post_like_count": 0,
                        "nft_count": 0,
                        "nft_royalty": 0,
                        "nft_coin": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "nft_gain": 0,
                        "sender_nft_bid_count": 0,
                        "receiver_nft_bid_count": 0,
                        "sender_message_count": 0,
                        "recipient_message_count": 67,
                        "sender_conversation_count": 0,
                        "recipient_conversation_count": 41,
                        "conversation_count": 41,
                        "time_to_profile": 18336,
                        "time_to_self_buy": 18336,
                        "time_to_first_buy": 18336,
                        "time_to_first_post": 0,
                        "fee": 3807,
                        "burned": 10514566,
                        "tx_count": 13453,
                        "transactor_tx_count": 3
                    },
                    "rank": {
                        "position": 2,
                        "change": 0
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.online.list

Get online accounts by latest transaction and by [**account.ping**](account.md#account.ping) endpoint notification.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>range</td><td></td><td>false</td><td>Represents list with min max values or default []. First index - min, second one - max. You can pass timestamps here to fetch online for latest 5 minutes only or for another time period. Maximum possible – 1 day.Re</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

List of account that are online in requested time frame.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s -data '[{"method":"account.online.list", "params": {"limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 1,
            "list": [
                {
                    "height": 94599,
                    "pubkey": "BC1YLitLy31oB6cWqBhusyvA1xwTC7pLG1FnHARiERFK6tGMP6w3Cit",
                    "balance": 912690,
                    "timestamp": 1641926884,
                    "profile": {
                        "timestamp": 1641926884,
                        "is_hidden": false,
                        "height": 94598,
                        "username": "EpicFail666",
                        "description": "вуыскшзешщт 1234",
                        "avatar_url": "http://media.overdeso.lo/avatar/aNa6HQ2oGmX",
                        "reward_points": 10000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 0,
                        "locked": 0,
                        "watermark": 0,
                        "price": 0
                    },
                    "dao": {
                        "disabled": false,
                        "restriction": 0,
                        "supply": "1d16daf5600"
                    },
                    "stat": {
                        "last_stat_ts": 1645435312,
                        "utxo_count": 14,
                        "level_points": 93,
                        "holder_count": 0,
                        "holding_count": 4,
                        "follower_count": 8,
                        "following_count": 8,
                        "coin_buy_count": 3,
                        "coin_buy_value": 564627,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "coin_gain": 0,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "receiver_coin_count": 15,
                        "receiver_coin_value": 441777,
                        "reward_coins": 0,
                        "reward_value": 0,
                        "dao": "1d16daf5600",
                        "dao_mint_count": 1,
                        "dao_burn_count": 1,
                        "dao_disable_count": 0,
                        "dao_restrict_count": 2,
                        "dao_holder_count": 1,
                        "dao_holding_count": 1,
                        "sender_dao_count": 0,
                        "receiver_dao_count": 0,
                        "sender_diamond_count": 29,
                        "sender_diamond_value": 3750000,
                        "receiver_diamond_count": 12,
                        "receiver_diamond_value": 1000000,
                        "post_count": 64,
                        "repost_count": 6,
                        "quote_count": 2,
                        "comment_count": 160,
                        "sender_post_like_count": 91,
                        "receiver_post_like_count": 93,
                        "nft_count": 0,
                        "nft_royalty": 0,
                        "nft_coin": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "nft_gain": 0,
                        "sender_nft_bid_count": 0,
                        "receiver_nft_bid_count": 0,
                        "sender_message_count": 183,
                        "recipient_message_count": 21,
                        "sender_conversation_count": 2,
                        "recipient_conversation_count": 0,
                        "conversation_count": 2,
                        "conversation_group_count": 0,
                        "time_to_profile": 0,
                        "time_to_self_buy": 0,
                        "time_to_first_buy": 241811,
                        "time_to_first_post": 3420918,
                        "fee": 4753457,
                        "burned": 1000058,
                        "tx_count": 790,
                        "transactor_tx_time": 1645435312,
                        "transactor_tx_height": 106091,
                        "transactor_tx_count": 708,
                        "tx_23_count": 0,
                        "tx_26_count": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "receiver_seed_count": 0,
                        "receiver_seed_value": 0,
                        "sender_connection_count": 466,
                        "sender_connection_value": 16666463,
                        "receiver_connection_count": 212,
                        "receiver_connection_value": 23232610
                    },
                    "online": {
                        "ts": 1645454628
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.autocomplete

Autocomplete account by its username or find existing account by pubkey

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>true</td><td>Username prefix to find or account pubkey</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

The method returns list compact account structures if found any using username prefix

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s -data '[{"method":"account.autocomplete", "params": {"username":"do", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "height": 1466,
                "pubkey": "BC1YLfwFyuEiLTEfqx7aJnPKttceVpiagCke7QW335mtTZ1QYhhYbqY",
                "balance": 19800,
                "timestamp": 1614605307,
                "profile": {
                    "timestamp": 1614605307,
                    "is_hidden": false,
                    "height": 1465,
                    "username": "do",
                    "description": "do",
                    "avatar_url": "https://overdeso.com/media/avatar/gE3EsxtbgSV",
                    "reward_points": 0,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 2714326952,
                    "locked": 19998001,
                    "watermark": 7236906254,
                    "price": 7367572
                }
            },
            {
                "height": 19574,
                "pubkey": "BC1YLgd69vQU3b6q3bhA8S4bGYKBppFG6J1B2QWjtdkNzPBbrvQ8VaL",
                "balance": 2997286,
                "timestamp": 1619679537,
                "profile": {
                    "timestamp": 1619679537,
                    "is_hidden": false,
                    "height": 19573,
                    "username": "do0_nct",
                    "description": "\n🛑 🛑 🛑 🛑 🛑 🛑\n\nThis BitClout profile is FREE to the REAL\n\ndo0_nct\n\nTo claim your account contact:\n Ray@ReservedProfile.com\n\n🛑 🛑 🛑 🛑 🛑 🛑\n",
                    "avatar_url": "https://overdeso.com/media/avatar/cD8hWLgXZLM",
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
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### account.upload.url

Get temporarely upload url for media content for account. This method REQUIRES reader state passed in header.

Limitations:&#x20;

1. Max video duration – 20 minutes.
2. The provided URL works for 10 minutes to use it.

Cloudflare docs for video uploading: [https://developers.cloudflare.com/stream/uploading-videos/direct-creator-uploads#direct-creator-upload-request-from-end-users](https://developers.cloudflare.com/stream/uploading-videos/direct-creator-uploads#direct-creator-upload-request-from-end-users)

Cloudflare docs for image uploading: [https://developers.cloudflare.com/images/cloudflare-images/upload-images/direct-creator-upload](https://developers.cloudflare.com/images/cloudflare-images/upload-images/direct-creator-upload)

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>One of: image or video</td></tr></tbody></table>

#### Response

Return structre with expire\_at and url

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -H 'X-Account-Username: donhardman' --data '[{"method":"account.upload.url", "params": {"type":"image"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "url": "https://upload.imagedelivery.net/98b16dd8-77c8-4507-88c3-755fada4d137",
            "expire_at": 1641143548
        }
    ]
]
```
{% endtab %}
{% endtabs %}
