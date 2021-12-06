---
description: Account related API methods.
---

# Account

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
            "coin": {
                "locked": 13506396730943,
                "price": 56714384896,
                "supply": 238147636715,
                "watermark": 244724729204
            },
            "height": 6042,
            "profile": {
                "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                "description": "\ud83d\udc8e\ud83d\ude4c",
                "height": 6044,
                "is_hidden": 0,
                "reward_points": 0,
                "stake_points": 12500,
                "username": "diamondhands"
            },
            "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
            "stat": {
                "coin_buy_count": 6,
                "coin_buy_value": 2976088833,
                "coin_sell_count": 2,
                "coin_sell_value": 60683183,
                "comment_count": 48,
                "follower_count": 2439,
                "following_count": 0,
                "holder_count": 825,
                "holding_count": 4,
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
                "post_count": 11,
                "quote_count": 0,
                "receiver_coin_count": 0,
                "receiver_coin_value": 0,
                "receiver_connection_count": 8191,
                "receiver_connection_value": 36962467593218,
                "receiver_diamond_count": 0,
                "receiver_diamond_value": 0,
                "receiver_seed_count": 1,
                "receiver_seed_value": 50000000,
                "repost_count": 0,
                "reward_coins": 0,
                "reward_value": 0,
                "sender_coin_count": 0,
                "sender_coin_value": 0,
                "sender_connection_count": 3,
                "sender_connection_value": 885750759,
                "sender_diamond_count": 0,
                "sender_diamond_value": 0,
                "sender_seed_count": 1,
                "sender_seed_value": 123000000,
                "tx_count": 4566
            }
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
curl -s --data '[{"method":"account.seeders", "params": {"username":"diamondhands", "type": "receiver", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
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
curl -s --data '[{"method":"account.connection.list", "params": {"username":"diamondhands", "type": "receiver", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 100,
            "list": [
                {
                    "count": 113,
                    "pubkey": "BC1YLiwCtwj9py5ekJFeXaxLmC8Z78qrBPiegZVqH9fRXh5hv7HFQpz",
                    "username": "ChingonETH",
                    "value": 19925096312304
                },
                {
                    "count": 20,
                    "pubkey": "BC1YLgScTfP6yTo8PcWW2uyxZBtTESbxonLBsDK9TTZ2e47YFmWn52d",
                    "username": "Stonehead",
                    "value": 9891141446768
                },
                {
                    "count": 30,
                    "pubkey": "BC1YLgT36phrdWaCLHV5mm65c1UgJJuHFcYcPEz1tK5mrtDmLBUf8ak",
                    "username": "Peps",
                    "value": 6370777170857
                },
                {
                    "count": 37,
                    "pubkey": "BC1YLhtAPCwD2wUawVc5n5miWuGo8159qrs5G9VE6FVc2ZPFryc2Vq4",
                    "username": "ArtofWar",
                    "value": 4232698819910
                },
                {
                    "count": 6,
                    "pubkey": "BC1YLgUU57aMVyfmrprFZicifoaH5QD8WdBWxtw5PWusD4Spe3CjwoS",
                    "username": null,
                    "value": 3434754199929
                },
                {
                    "count": 23,
                    "pubkey": "BC1YLiWhFc7jgCAiaY39Uer7kpTdDMSyPH9zQma9N4hKXyXeWX5cmh1",
                    "username": "GalaMar",
                    "value": 2964212949677
                },
                {
                    "count": 27,
                    "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8",
                    "username": "RajLahoti",
                    "value": 2958865247508
                },
                {
                    "count": 15,
                    "pubkey": "BC1YLgLu3J4EUf7xXZ2KmT332tLboPxXZS8cE4wJY7ifx8Ccsc9dPxW",
                    "username": null,
                    "value": 2076935212298
                },
                {
                    "count": 10,
                    "pubkey": "BC1YLgrg6eoEqj76JX6FfW9dYLZ5ZBAkmZy7fMz3r7nfKDpwKHSwJnt",
                    "username": "MantisToboggan",
                    "value": 1978669741283
                },
                {
                    "count": 10,
                    "pubkey": "BC1YLjDphVAw4TYiwv24tgd9PjuKAoiWCSxomraKerbRibCvZAGRoZV",
                    "username": "moysha_mk",
                    "value": 1869918071287
                }
            ],
            "value": 0
        }
    ]
]
```
{% endtab %}
{% endtabs %}



