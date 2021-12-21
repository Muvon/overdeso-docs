---
description: Account related API methods.
---

# 👤 Account

### account.get

The method allows to get profile by username or account by public key in base58 check format.

The method requires one of **username** or **pubkey** to be passed in request body.

#### Request params <a href="#request-params" id="request-params"></a>

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr></tbody></table>

#### Response

The method returns account stracture with fields: pubkey, height, profile, coin, stat.

{% tabs %}
{% tab title="CURL" %}
```shell
curl --data '[{"method":"account.get", "params": {"username":"diamondhands"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "balance": 1202499588544,
            "coin": {
                "locked": 4634807406285,
                "price": 28109253787,
                "supply": 164885465878,
                "watermark": 255810788786
            },
            "height": 6042,
            "profile": {
                "avatar_url": "https://overdeso.com/media/avatar/Xs8Q75nrKj5",
                "description": "\ud83d\udc8e\ud83d\ude4c",
                "height": 6044,
                "is_hidden": false,
                "reward_points": 0,
                "stake_points": 12500,
                "timestamp": 1615574830,
                "username": "diamondhands"
            },
            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
            "stat": {
                "coin_buy_count": 81,
                "coin_buy_value": 8611846815339,
                "coin_sell_count": 2,
                "coin_sell_value": 60683183,
                "comment_count": 565,
                "follower_count": 23795,
                "following_count": 31,
                "holder_count": 3700,
                "holding_count": 2659,
                "nft_buy_count": 12,
                "nft_buy_value": 51738588404,
                "nft_coin": 117500000000,
                "nft_count": 3,
                "nft_gain": 467500000000,
                "nft_mint_count": 2,
                "nft_mint_value": 467500000000,
                "nft_royalty": 0,
                "nft_sell_count": 0,
                "nft_sell_value": 0,
                "post_count": 89,
                "quote_count": 34,
                "receiver_coin_count": 9259,
                "receiver_coin_value": 619817135916,
                "receiver_connection_count": 133398,
                "receiver_connection_value": 139102999315321,
                "receiver_diamond_count": 29126,
                "receiver_diamond_value": 155657369222,
                "receiver_seed_count": 1,
                "receiver_seed_value": 50000000,
                "repost_count": 8,
                "reward_coins": 0,
                "reward_value": 0,
                "sender_coin_count": 1644,
                "sender_coin_value": 835936498462,
                "sender_connection_count": 362,
                "sender_connection_value": 3509377349917,
                "sender_diamond_count": 6463,
                "sender_diamond_value": 101771508175,
                "sender_seed_count": 3,
                "sender_seed_value": 1124000000,
                "tx_count": 71641,
                "utxo_count": 5147
            },
            "timestamp": 1615574505
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.list

Get list of account sorted by wanted field in descending way (hight to low).

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>is_hidden</td><td></td><td>false</td><td>Default is false</td></tr><tr><td>sorting</td><td></td><td>false</td><td>Can be one of: locked, profile_ts, balance. Default is locked.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

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
            "count": 102343,
            "list": [
                {
                    "balance": 1446756063,
                    "coin": {
                        "locked": 33061863037214,
                        "price": 103011361141,
                        "supply": 320953559596,
                        "watermark": 453559032340
                    },
                    "height": 2,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/hu6AQwwyneq",
                        "description": "",
                        "height": 2,
                        "is_hidden": false,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "timestamp": 1614598233,
                        "username": "elonmusk"
                    },
                    "pubkey": "BC1YLiFNARSWF6qtXM5acrS7q8VWPeeS2gycVBtqLALkE4c1V3kx4US",
                    "stat": {
                        "coin_buy_count": 2,
                        "coin_buy_value": 79595351183,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "comment_count": 0,
                        "follower_count": 20277,
                        "following_count": 0,
                        "holder_count": 8590,
                        "holding_count": 66,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_coin": 0,
                        "nft_count": 0,
                        "nft_gain": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_royalty": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "post_count": 0,
                        "quote_count": 0,
                        "receiver_coin_count": 84,
                        "receiver_coin_value": 15732622134,
                        "receiver_connection_count": 42552,
                        "receiver_connection_value": 326182002560736,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 1,
                        "receiver_seed_value": 20000,
                        "repost_count": 0,
                        "reward_coins": 0,
                        "reward_value": 0,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 0,
                        "sender_connection_value": 0,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 42642,
                        "utxo_count": 36
                    },
                    "timestamp": 1614598233
                },
                {
                    "balance": 17779739570,
                    "coin": {
                        "locked": 18226560161314,
                        "price": 69258014669,
                        "supply": 263168966771,
                        "watermark": 353048906645
                    },
                    "height": 5769,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/bNpKqDCBDRf",
                        "description": "",
                        "height": 5840,
                        "is_hidden": false,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "timestamp": 1615529337,
                        "username": "naval"
                    },
                    "pubkey": "BC1YLgVNKrgTYt1QaeTCW46KMRfCNEAEKrgWdEDUKSQsd42JfQMNncs",
                    "stat": {
                        "coin_buy_count": 1,
                        "coin_buy_value": 95145650200,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "comment_count": 0,
                        "follower_count": 6812,
                        "following_count": 0,
                        "holder_count": 1237,
                        "holding_count": 23,
                        "nft_buy_count": 0,
                        "nft_buy_value": 0,
                        "nft_coin": 0,
                        "nft_count": 0,
                        "nft_gain": 0,
                        "nft_mint_count": 0,
                        "nft_mint_value": 0,
                        "nft_royalty": 0,
                        "nft_sell_count": 0,
                        "nft_sell_value": 0,
                        "post_count": 0,
                        "quote_count": 0,
                        "receiver_coin_count": 24,
                        "receiver_coin_value": 26346340418,
                        "receiver_connection_count": 10843,
                        "receiver_connection_value": 86309332434857,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 1,
                        "receiver_seed_value": 94822628903,
                        "repost_count": 0,
                        "reward_coins": 30793004148,
                        "reward_value": 5688338959697,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 1,
                        "sender_connection_value": 100000000,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 10871,
                        "utxo_count": 238
                    },
                    "timestamp": 1615511001
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
            "count": 1,
            "list": [
                {
                    "output": [
                        "3JuEU8HXcjzfV9Y8v1vTiVr6GRsTRvq11dk7vUQu5ogcCMaUKMV9ab",
                        0
                    ],
                    "value": 80799439128
                }
            ],
            "value": 80799439128
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.follow.list

Find accounts which the person following or which following that person.

The method requires one of **username** or **pubkey** to be passed in request body.

#### Request params <a href="#request-params" id="request-params"></a>

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be following or follower.</td></tr><tr><td>expand</td><td></td><td>false</td><td>If set to true we expand account info instead of just pubkey and username returned in item. Default is false.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returnes list of follower or following accounts.

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.follow.list", "params": {"username":"diamondhands", "type": "following", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 21,
            "list": [
                {
                    "pubkey": "BC1YLi6LpXTemAG8T9ptyWAkMywrjynwZcKjB5DkDXxrsG5kgAwAqxq",
                    "username": "maebeam"
                },
                {
                    "pubkey": "BC1YLiU9Wpk8c7pVx7GCu8fae6AQhdUrGYcWc1Wz9V56HbCi7RPr887",
                    "username": "balajis"
                },
                {
                    "pubkey": "BC1YLi3P5VRwVaABUCrQQHEEUoQGoAUpcS272Rb16MDH1Uy8Kg9q3sX",
                    "username": "helenowen"
                },
                {
                    "pubkey": "BC1YLhqEhWvNnwW9TBqXURFqwkdpUYKrMVgTHQzopF5rRBDcD1LLSUp",
                    "username": "artz"
                },
                {
                    "pubkey": "BC1YLj4iUraQabhUBT8kS1gCieXhD1GGXeFCcU3qM3MGgf7GwBJ9Va7",
                    "username": "craig"
                },
                {
                    "pubkey": "BC1YLgHUYA2phkKYS6LdLLhkfGW7XkKX2D1Ktp5HVT8TpNGcah9KexY",
                    "username": "dharmann"
                },
                {
                    "pubkey": "BC1YLjERk6o1wsh8NMhKKebBsyzjBVGSMwMy9e45VgZUmwWaTWWZcRT",
                    "username": "Drseuss"
                },
                {
                    "pubkey": "BC1YLhoXx7AxSDdcz8mhFKmcP5jzA2Z8tXDjUTsttGe7rE7sK3Ures7",
                    "username": "BennyBlanco"
                },
                {
                    "pubkey": "BC1YLg5xgL7PAToY7dNrxqRmtAarJvBBZKJTkreuv2eLvCppf58Pwn9",
                    "username": "Doodles"
                },
                {
                    "pubkey": "BC1YLiQqFd4ro1jw3XTZ4zxMjEQka7NXy4aTc8Km1oeDHwjBn2kXrDy",
                    "username": "rrhoover"
                }
            ]
        }
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
curl -s --data '[{"method":"account.seed.list", "params": {"username":"diamondhands", "type": "receiver", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 1,
            "list": [
                {
                    "pubkey": "BC1YLhSkfH28QrMAVkbejMUZELwkAEMwr2FFwhEtofHvzHRtP6rd7s6",
                    "username": "merlin",
                    "value": 50000000
                }
            ],
            "value": 50000000
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
            "count": 133398,
            "list": [
                {
                    "count": 118,
                    "pubkey": "BC1YLiwCtwj9py5ekJFeXaxLmC8Z78qrBPiegZVqH9fRXh5hv7HFQpz",
                    "username": "WhaleSharkIsSCAMMER",
                    "value": 19925096312304
                },
                {
                    "count": 31,
                    "pubkey": "BC1YLfmgKvbo5fmZzXV4hcmBsWGbKHU3rvSvGkpvjZTuktF9XhEgc6n",
                    "username": "whoami",
                    "value": 12134445221924
                }
            ],
            "value": 0
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.holding.list

Get account creator coins holding or those who hold it.

The method requires one of **username** or **pubkey** to be passed in request body.

#### Request params <a href="#request-params" id="request-params"></a>

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be holding or holder. First one is for fetching holding account and second one for fetching holders of an account.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns creator coin holdings for account or holder list for creator.

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.holding.list", "params": {"username":"diamondhands", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 4,
            "list": [
                {
                    "account": {
                        "account": {
                            "height": 5929,
                            "pubkey": "BC1YLhrtptZUpJDgXJrdQdojctfTE2GdATqjW2259p7oFN45YFbH3Zp"
                        },
                        "coin": {
                            "locked": 1019099654107,
                            "price": 10126933450,
                            "supply": 100632601086,
                            "watermark": 117818600424
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/8wURLVXw1P",
                            "description": "Sell at your own risk. Founder at TH3RD BRAIN. Head of Activation at Community. Happy Google finally stopped saying I was the founder of this thing \ud83d\ude02 @diamondhands for President",
                            "height": 6180,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "jakeudell"
                        }
                    },
                    "holding": {
                        "coins": 147428805,
                        "has_purchased": 1,
                        "spend": 2077322200
                    }
                },
                {
                    "account": {
                        "account": {
                            "height": 0,
                            "pubkey": "BC1YLiWhFc7jgCAiaY39Uer7kpTdDMSyPH9zQma9N4hKXyXeWX5cmh1"
                        },
                        "coin": {
                            "locked": 865848244213,
                            "price": 9084367703,
                            "supply": 95311888778,
                            "watermark": 103782359872
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/9MehwovZoi",
                            "description": "Seeding early adopters to build a vibrant creator community, by the people for the people. Buying myself back.",
                            "height": 6061,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "GalaMar"
                        }
                    },
                    "holding": {
                        "coins": 24480942,
                        "has_purchased": 1,
                        "spend": 755208922
                    }
                },
                {
                    "account": {
                        "account": {
                            "height": 2,
                            "pubkey": "BC1YLiFNARSWF6qtXM5acrS7q8VWPeeS2gycVBtqLALkE4c1V3kx4US"
                        },
                        "coin": {
                            "locked": 79695133404558,
                            "price": 185191671630,
                            "supply": 430338646998,
                            "watermark": 453559032340
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/AGRjTR2Rb2",
                            "description": "",
                            "height": 2,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "elonmusk"
                        }
                    },
                    "holding": {
                        "coins": 141915,
                        "has_purchased": 1,
                        "spend": 75320550
                    }
                },
                {
                    "account": {
                        "account": {
                            "height": 1495,
                            "pubkey": "BC1YLiVuAdFkfRz7XdEuf9tPSmNt7FXGSLFNvtjRA3HCtuCGEKijaZH"
                        },
                        "coin": {
                            "locked": 212265714,
                            "price": 362847374358974,
                            "supply": 585,
                            "watermark": 8015147004
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/8J9F64MHZE",
                            "description": "salomon",
                            "height": 1495,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "salomon"
                        }
                    },
                    "holding": {
                        "coins": 7,
                        "has_purchased": 1,
                        "spend": 7541837
                    }
                },
                {
                    "account": {
                        "account": {
                            "height": 6042,
                            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                        },
                        "coin": {
                            "locked": 13017215927159,
                            "price": 55336577735,
                            "supply": 235237097411,
                            "watermark": 244724729204
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/A7cKMcdG1K",
                            "description": "\ud83d\udc8e\ud83d\ude4c",
                            "height": 6044,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "diamondhands"
                        }
                    },
                    "holding": {
                        "coins": 0,
                        "has_purchased": 1,
                        "spend": 0
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### account.trade.list

Get information about creator coin for account as investor or as creator.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>type</td><td></td><td>false</td><td>Can be investor or creator. First one for fetching information for account as investor and second one as creator.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of coins and account infos.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.trade.list", "params": {"username":"diamondhands", "limit": 5}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 123,
            "list": [
                {
                    "account": {
                        "account": {
                            "balance": 19854068267,
                            "height": 8387,
                            "pubkey": "BC1YLjP9gbLxZkhYGYuDj2YXb3gNaAaNvFfYiwUzmXqptWkNxM6wedK"
                        },
                        "coin": {
                            "locked": 556706877961,
                            "price": 6767338559,
                            "supply": 82263784068,
                            "watermark": 116129783019
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/UgqpKctLRxg",
                            "description": "UI/UX/Design guy.\n\nFor every 1,000 of coin you buy, I design one screen for your app/website.\n\u2013\u2014\u2014\nCreator of @cloutopolygame",
                            "height": 8391,
                            "is_hidden": 0,
                            "reward_points": 1200,
                            "stake_points": 12500,
                            "username": "charliehilton"
                        }
                    },
                    "coin": {
                        "coins": 267906829,
                        "gain": 0,
                        "operation": "buy",
                        "value": 5925630021
                    },
                    "id": "3JuETaZukgKnNgL7GseRzP6c66QjNyC7QJAzdAS9VVP8x1XizC3Avd",
                    "receiver": {
                        "account": {
                            "balance": 10305486356,
                            "height": 6042,
                            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                        },
                        "coin": {
                            "locked": 5020816498124,
                            "price": 29321292721,
                            "supply": 171234486347,
                            "watermark": 255810788786
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8v13xRi",
                            "description": "\ud83d\udc8e\ud83d\ude4c",
                            "height": 6044,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "diamondhands"
                        }
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 428407196435,
                            "height": 8951,
                            "pubkey": "BC1YLh6kmsfCN4WcZ5eqPTJyYUGLJiN3iHj614788Yc461XRgrYJZdU"
                        },
                        "coin": {
                            "locked": 719361637393,
                            "price": 8028449821,
                            "supply": 89601561126,
                            "watermark": 89601561126
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/ahySPXEFsnC",
                            "description": "The Talent Fund guy. @TheTalentFundII, @TheTalentFund, and @TheTalentFundI\n\nAlso Maebeam's #1 fan!\n\nManaging Member, Sunset Digital Asset Management. ",
                            "height": 8951,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "reade"
                        }
                    },
                    "coin": {
                        "coins": 221950972,
                        "gain": 0,
                        "operation": "buy",
                        "value": 5925630021
                    },
                    "id": "3JuETJZ1Ne5PdeiKKK9eb9K89TGxqtFxKYa2CeaXJTiEn2GxaNKrzx",
                    "receiver": {
                        "account": {
                            "balance": 10305486356,
                            "height": 6042,
                            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                        },
                        "coin": {
                            "locked": 5020816498124,
                            "price": 29321292721,
                            "supply": 171234486347,
                            "watermark": 255810788786
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8v13xRi",
                            "description": "\ud83d\udc8e\ud83d\ude4c",
                            "height": 6044,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "diamondhands"
                        }
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 1442643611442,
                            "height": 5929,
                            "pubkey": "BC1YLhrtptZUpJDgXJrdQdojctfTE2GdATqjW2259p7oFN45YFbH3Zp"
                        },
                        "coin": {
                            "locked": 7114682975512,
                            "price": 36991668347,
                            "supply": 192332038357,
                            "watermark": 209116187783
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/SgPYb7vRLj6",
                            "description": "Founder at TH3RD BRAIN. Head of Activation at Community.com - Text me 3125007854. Happy Google finally stopped saying I was the founder of this thing \ud83d\ude02 @diamondhands for President",
                            "height": 6180,
                            "is_hidden": 0,
                            "reward_points": 1500,
                            "stake_points": 12500,
                            "username": "jakeudell"
                        }
                    },
                    "coin": {
                        "coins": 44839,
                        "gain": 0,
                        "operation": "buy",
                        "value": 5855527
                    },
                    "id": "3JuETZwsYVuHjkjgdT6yUcamzzweeJE4s9zBMtRQVr6sFY7A9pYf13",
                    "receiver": {
                        "account": {
                            "balance": 10305486356,
                            "height": 6042,
                            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                        },
                        "coin": {
                            "locked": 5020816498124,
                            "price": 29321292721,
                            "supply": 171234486347,
                            "watermark": 255810788786
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8v13xRi",
                            "description": "\ud83d\udc8e\ud83d\ude4c",
                            "height": 6044,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "diamondhands"
                        }
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 761731067,
                            "height": 11699,
                            "pubkey": "BC1YLgoFQSnvjVzMZqYs9aPEAGYFr7psFHKNhL486Zpgc4FcJ6VE5rL"
                        },
                        "coin": {
                            "locked": 40584402610,
                            "price": 1180971938,
                            "supply": 34365255671,
                            "watermark": 38726247829
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/gjBTSyVBzZr",
                            "description": "homeofjake.com\n\npodcast: podcasts.apple.com/us/podcast/pod-of-jake/id1525087226",
                            "height": 11699,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "blogofjake"
                        }
                    },
                    "coin": {
                        "coins": 1487602,
                        "gain": 0,
                        "operation": "buy",
                        "value": 5855527
                    },
                    "id": "3JuET7KRP3tF8YBimDjTXGr7VgvxwheLXhMwtCymaU5bWmWtmJ6bhz",
                    "receiver": {
                        "account": {
                            "balance": 10305486356,
                            "height": 6042,
                            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                        },
                        "coin": {
                            "locked": 5020816498124,
                            "price": 29321292721,
                            "supply": 171234486347,
                            "watermark": 255810788786
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8v13xRi",
                            "description": "\ud83d\udc8e\ud83d\ude4c",
                            "height": 6044,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "diamondhands"
                        }
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 10305486356,
                            "height": 6042,
                            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                        },
                        "coin": {
                            "locked": 5020816498124,
                            "price": 29321292721,
                            "supply": 171234486347,
                            "watermark": 255810788786
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8v13xRi",
                            "description": "\ud83d\udc8e\ud83d\ude4c",
                            "height": 6044,
                            "is_hidden": 0,
                            "reward_points": 0,
                            "stake_points": 12500,
                            "username": "diamondhands"
                        }
                    },
                    "coin": {
                        "coins": 59707,
                        "gain": -5249374,
                        "operation": "transfer",
                        "value": 5249374
                    },
                    "id": "3JuEUNikzG4DCWC9NPnviPQL2Uc31YjaspjiBMrbtSern2GDrwwrXW",
                    "receiver": {
                        "account": {
                            "balance": 2875914344,
                            "height": 22567,
                            "pubkey": "BC1YLigt4BuFfyVSBxKYGgUf8x9cGdC5TP4A7pyxwxA7RNRnCqcts1k"
                        },
                        "coin": {
                            "locked": 13038912602,
                            "price": 553980365,
                            "supply": 23536777507,
                            "watermark": 23603583701
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/biFsUpPCJ2p",
                            "description": "Dealer of \ud83d\udd25 memes \n\nOn a quest to make memes the universal currency so that I can retire on a beach as a MEMEillionaire \ud83d\udcb0\n\nFR 10%",
                            "height": 22570,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "MyMemeDealer"
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

### account.stat.list

Get account historical stats for username or public key.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>period</td><td></td><td>false</td><td>Aggregation period. One of: hour, day, month. Default is hour</td></tr><tr><td>start_at</td><td></td><td>false</td><td>Timestamp to start our lookup. Default is 1610948544 that is genesis block timestamp. That means we fetch from first stat record.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns statistic related data in chronological order (low to high).

**count** – how many rows total in your request.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"account.stat.list", "params": {"username":"diamondhands", "period": "hour", "start_at": 1616174306, "limit": 5}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 5,
            "list": [
                {
                    "coin_buy_count": 3,
                    "coin_buy_value": 2138017524,
                    "coin_sell_count": 2,
                    "coin_sell_value": 60683183,
                    "comment_count": 25,
                    "follower_count": 307,
                    "following_count": 0,
                    "holder_count": 178,
                    "holding_count": 1,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_coin": 0,
                    "nft_count": 0,
                    "nft_gain": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_royalty": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "post_count": 5,
                    "quote_count": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "receiver_connection_count": 1046,
                    "receiver_connection_value": 9289250704892,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "receiver_seed_count": 1,
                    "receiver_seed_value": 50000000,
                    "repost_count": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "sender_connection_count": 2,
                    "sender_connection_value": 2200322200,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "sender_seed_count": 1,
                    "sender_seed_value": 123000000,
                    "ts": 1616173200,
                    "tx_count": 689,
                    "utxo_count": 0
                },
                {
                    "coin_buy_count": 3,
                    "coin_buy_value": 2138017524,
                    "coin_sell_count": 2,
                    "coin_sell_value": 60683183,
                    "comment_count": 25,
                    "follower_count": 311,
                    "following_count": 0,
                    "holder_count": 179,
                    "holding_count": 1,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_coin": 0,
                    "nft_count": 0,
                    "nft_gain": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_royalty": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "post_count": 5,
                    "quote_count": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "receiver_connection_count": 1064,
                    "receiver_connection_value": 9302084296947,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "receiver_seed_count": 1,
                    "receiver_seed_value": 50000000,
                    "repost_count": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "sender_connection_count": 2,
                    "sender_connection_value": 2200322200,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "sender_seed_count": 1,
                    "sender_seed_value": 123000000,
                    "ts": 1616176800,
                    "tx_count": 700,
                    "utxo_count": 0
                },
                {
                    "coin_buy_count": 3,
                    "coin_buy_value": 2138017524,
                    "coin_sell_count": 2,
                    "coin_sell_value": 60683183,
                    "comment_count": 25,
                    "follower_count": 316,
                    "following_count": 0,
                    "holder_count": 180,
                    "holding_count": 1,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_coin": 0,
                    "nft_count": 0,
                    "nft_gain": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_royalty": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "post_count": 5,
                    "quote_count": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "receiver_connection_count": 1078,
                    "receiver_connection_value": 9373137176387,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "receiver_seed_count": 1,
                    "receiver_seed_value": 50000000,
                    "repost_count": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "sender_connection_count": 2,
                    "sender_connection_value": 2200322200,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "sender_seed_count": 1,
                    "sender_seed_value": 123000000,
                    "ts": 1616180400,
                    "tx_count": 710,
                    "utxo_count": 0
                },
                {
                    "coin_buy_count": 3,
                    "coin_buy_value": 2138017524,
                    "coin_sell_count": 2,
                    "coin_sell_value": 60683183,
                    "comment_count": 25,
                    "follower_count": 348,
                    "following_count": 0,
                    "holder_count": 189,
                    "holding_count": 1,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_coin": 0,
                    "nft_count": 0,
                    "nft_gain": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_royalty": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "post_count": 5,
                    "quote_count": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "receiver_connection_count": 1148,
                    "receiver_connection_value": 9618079558666,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "receiver_seed_count": 1,
                    "receiver_seed_value": 50000000,
                    "repost_count": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "sender_connection_count": 2,
                    "sender_connection_value": 2200322200,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "sender_seed_count": 1,
                    "sender_seed_value": 123000000,
                    "ts": 1616184000,
                    "tx_count": 760,
                    "utxo_count": 0
                },
                {
                    "coin_buy_count": 3,
                    "coin_buy_value": 2138017524,
                    "coin_sell_count": 2,
                    "coin_sell_value": 60683183,
                    "comment_count": 25,
                    "follower_count": 348,
                    "following_count": 0,
                    "holder_count": 190,
                    "holding_count": 1,
                    "nft_buy_count": 0,
                    "nft_buy_value": 0,
                    "nft_coin": 0,
                    "nft_count": 0,
                    "nft_gain": 0,
                    "nft_mint_count": 0,
                    "nft_mint_value": 0,
                    "nft_royalty": 0,
                    "nft_sell_count": 0,
                    "nft_sell_value": 0,
                    "post_count": 5,
                    "quote_count": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "receiver_connection_count": 1150,
                    "receiver_connection_value": 9621984149885,
                    "receiver_diamond_count": 0,
                    "receiver_diamond_value": 0,
                    "receiver_seed_count": 1,
                    "receiver_seed_value": 50000000,
                    "repost_count": 0,
                    "reward_coins": 0,
                    "reward_value": 0,
                    "sender_coin_count": 0,
                    "sender_coin_value": 0,
                    "sender_connection_count": 2,
                    "sender_connection_value": 2200322200,
                    "sender_diamond_count": 0,
                    "sender_diamond_value": 0,
                    "sender_seed_count": 1,
                    "sender_seed_value": 123000000,
                    "ts": 1616187600,
                    "tx_count": 761,
                    "utxo_count": 0
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
