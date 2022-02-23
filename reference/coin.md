---
description: Coin related API is gonna be here
---

# 🪙 Coin

### coin.holding.get

Get holding information for creator coin or DAO for wanter pair of investor/creator

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>Can be one of <code>creator</code> or <code>dao</code></td></tr><tr><td>account</td><td></td><td>true</td><td>Investor account </td></tr><tr><td>creator</td><td></td><td>true</td><td>Creator account</td></tr></tbody></table>

#### Response

The method returns holding info for request pair of investor and creator;

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"coin.holding.get", "params": {"type": "creator", "account":"diamondhands", "creator":"maebeam"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "price": 10785351383,
            "coins": 508964325,
            "spend": 5489359087,
            "has_purchased": true
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### coin.holding.list

Get account creator coins / DAO holding or those who hold it.

#### Request params <a href="#request-params" id="request-params"></a>

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>Can be one of: <code>creator</code> or <code>dao</code></td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>position</td><td></td><td>false</td><td>Can be holding or holder. First one is for fetching <code>holding</code> account and second one for fetching <code>holder</code> of an account.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns creator coin holdings for account or holder list for creator.

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"coin.holding.list", "params": {"type": "creator", "account":"diamondhands", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 1472,
            "list": [
                {
                    "coins": 3990047612,
                    "spend": 5710975084,
                    "has_purchased": true,
                    "account": {
                        "height": 6078,
                        "pubkey": "BC1YLiheqL6jdqs9WK3ctBDxMR6bXv4q6ybFhFnmJnbX7K6vnT8BHBA",
                        "balance": 32082956160,
                        "timestamp": 1615599324,
                        "profile": {
                            "timestamp": 1617326847,
                            "is_hidden": false,
                            "height": 11787,
                            "username": "derekdolin",
                            "description": "Director of Strategy & 1st US Employee @threesixzero|\nFmr. Entrepreneur-in-Residence @ Peter Diamandis | Angel Investor | Passionate about helping early-stage companies grow.",
                            "avatar_url": "http://media.overdeso.lo/avatar/NfbbnjuCwK3",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 21991409789,
                            "locked": 10635540757,
                            "watermark": 38252878990,
                            "price": 483622508
                        }
                    }
                },
                {
                    "coins": 2421634842,
                    "spend": 0,
                    "has_purchased": false,
                    "account": {
                        "height": 12530,
                        "pubkey": "BC1YLgQvYpr3vamYDGiJMHA47DMi54Hx5kVeRRm3Dd4ZZHKcr8wEArk",
                        "balance": 106365,
                        "timestamp": 1617536193,
                        "profile": {
                            "timestamp": 1617537719,
                            "is_hidden": false,
                            "height": 12534,
                            "username": "BitYourSocialMedia",
                            "description": "☑ If you want to understand the universe,think in terms of energy,frequency and vibration\n3-bitclout 6-plan to action 9-manifest it\n@p2p \n@diamondhands\ntwitter.com/fatjonshaha\n\n",
                            "avatar_url": "http://media.overdeso.lo/avatar/QW81Qbdgcys",
                            "reward_points": 3600,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 7066495751,
                            "locked": 352868218,
                            "watermark": 11800022927,
                            "price": 49935389
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

### coin.operation.list

Get information about creator / DAO coin for account as investor or as creator.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>Can be one of : <code>creator</code> or <code>dao</code></td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>position</td><td></td><td>false</td><td>Can be investor or creator. First one for fetching information for account as investor and second one as creator.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of coins and account infos.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"coin.operation.list", "params": {"type": "creator", "account":"diamondhands", "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
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
