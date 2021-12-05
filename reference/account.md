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
curl --data '[{"method":"account.get", "params": {"username":"donhardman"}}]' http://api.overdeso.lo/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "coin": {
                "locked": 23437529569,
                "price": 818982639,
                "supply": 28617858834,
                "watermark": 28617858834
            },
            "height": 11962,
            "profile": {
                "avatar": "data:image/webp;base64,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",
                "description": "Free runner & Dev head\n\n@muvon founder\n@cloutangel co-founder",
                "height": 11965,
                "is_hidden": 0,
                "reward_points": 1021,
                "stake_points": 12500,
                "username": "donhardman"
            },
            "pubkey": "BC1YLgteRL8SgzZLmPyx6hK1tt6XXtaE3m5qAy9GFhP3eGtXmjqEULB",
            "stat": {
                "comment_count": 303,
                "follower_count": 1587,
                "following_count": 360,
                "holder_count": 211,
                "holding_count": 20,
                "nft_buy": 0,
                "nft_coin": 0,
                "nft_gain": 0,
                "nft_mint": 0,
                "nft_royalty": 0,
                "nft_sell": 0,
                "post_count": 276,
                "quote_count": 75,
                "receiver_diamond_count": 665,
                "receiver_diamond_value": 1096854912,
                "repost_count": 111,
                "reward_coins": 3653658018,
                "reward_value": 3136338112,
                "sender_diamond_count": 932,
                "sender_diamond_value": 370912360
            }
        }
    ]
]
```
{% endtab %}

{% tab title="Second Tab" %}

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

{% tab title="Second Tab" %}

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

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}



