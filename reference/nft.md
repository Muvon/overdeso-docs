---
description: NFT related methods
---

# ✨ NFT

### nft.get

Fetch information about NFT by its serial number and post hash

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format where NFT was minted</td></tr><tr><td>serial</td><td></td><td>true</td><td>Serial NO of nft</td></tr></tbody></table>

#### Response

The method returns information about requested NFT

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"nft.get", "params": {"hash": "902018d6de32fb3f4f578fb53aa179325bd9d07fae0502279a6d0c27b01f5664", "serial": 3}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "serial": 3,
            "is_burned": true,
            "is_pending": false,
            "is_selling": false,
            "min_bid": 0,
            "last_accepted_bid": 0
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### nft.list

Get NFT list for related post by its hash

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format where NFT was minted</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of NFTs for related post hash.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"nft.list", "params": {"hash": "902018d6de32fb3f4f578fb53aa179325bd9d07fae0502279a6d0c27b01f5664", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 100,
            "list": [
                {
                    "serial": 1,
                    "is_burned": false,
                    "is_pending": false,
                    "is_selling": false,
                    "min_bid": 0,
                    "last_accepted_bid": 0
                },
                {
                    "serial": 2,
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "min_bid": 0,
                    "last_accepted_bid": 0
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### nft.bid.list

Get bids for NFT with requested post hash or post hash and serial

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format where NFT was minted</td></tr><tr><td>serial</td><td></td><td>false</td><td>Serial of NFT to get bids for. If omitted we get bids for all serials</td></tr><tr><td>sorting</td><td></td><td>false</td><td>One of: value, created_at. Default is value. Sorting always performs in desc order.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns list of NFT bids and bidder information as list sorted by value of bid or created time (high to low).

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"nft.bid.list", "params": {"hash": "d66a0aedaaf51bd992262f53c682e2608acbdafeb52bb4f0c1f4dfe85e8c440c", "limit": 5}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 2,
            "list": [
                {
                    "bid": {
                        "serial": 1,
                        "value": 9994003
                    },
                    "account": {
                        "height": 15301,
                        "pubkey": "BC1YLgrXFcDjxmS6qB7k1dbW9aD69GoQ6cYJ4QqwELpXtct1rPX5dub",
                        "balance": 10712539,
                        "timestamp": 1618392126,
                        "profile": {
                            "timestamp": 1618392126,
                            "is_hidden": false,
                            "height": 15300,
                            "username": "OTZGALLERY",
                            "description": "Contemporary art polymath + VECTOR\nhttps://linktr.ee/LIPF\ninstagram.com/outsidethe_zone\nhttps://opensea.io/OTZ_GALLERY\nhttps://www.youtube.com/channel/UC6bH7IgPZjvYOZ7YTxI5t\n",
                            "avatar_url": "https://overdeso.com/media/avatar/X2Ye1jK63hb",
                            "reward_points": 2000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 7069908548,
                            "locked": 358895157,
                            "watermark": 14079805699,
                            "price": 50763762
                        }
                    }
                },
                {
                    "bid": {
                        "serial": 1,
                        "value": 9124087
                    },
                    "account": {
                        "height": 34783,
                        "pubkey": "BC1YLit4H3VZDu1a5DeoXQhjvYa3rtCYza3RUPkeNWpHDS6XLQNiaMT",
                        "balance": 69328901,
                        "timestamp": 1623939677,
                        "profile": {
                            "timestamp": 1623951347,
                            "is_hidden": false,
                            "height": 34813,
                            "username": "NFTCurator",
                            "description": "Discover-Defend-Celebrate\n\nBuild a NFT Artist Collection\n\nNew NFT Artists Daily- VERIFIED\nTop Coin Holders- Artist Studio Visits\n\n\n\n@WhereArtWorks Project by @just_in",
                            "avatar_url": "https://overdeso.com/media/avatar/eZ6uZ5PyK5K",
                            "reward_points": 2200,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 632277545,
                            "locked": 252769,
                            "watermark": 45864375575,
                            "price": 399775
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

### nft.trade.list

Get trades for NFT.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format where NFT was minted</td></tr><tr><td>serial</td><td></td><td>false</td><td>Serial of NFT to get bids for. If omitted we get bids for all serials</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch. Default is 50</td></tr></tbody></table>

#### Response

Returns list of trades for NFT with serial or for all nfts for post.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"nft.trade.list", "params": {"hash": "d66a0aedaaf51bd992262f53c682e2608acbdafeb52bb4f0c1f4dfe85e8c440c", "limit": 5}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 1,
            "list": [
                {
                    "nft": {
                        "serial": 1,
                        "is_burned": false,
                        "is_pending": false,
                        "is_selling": true,
                        "min_bid": 99000000000,
                        "last_accepted_bid": 1261000000
                    },
                    "trade": {
                        "seller_value": 1008800000,
                        "buyer_value": 1261000000,
                        "creator_value": 126100000,
                        "coin_value": 126100000,
                        "gain": 1008800000
                    },
                    "account": {
                        "height": 14973,
                        "pubkey": "BC1YLgzcfyi5GZoMb9xoVzDCMy9KEzzvTqoJzRrVDfhWE2FfFubxaVm",
                        "balance": 194658476187,
                        "timestamp": 1618285360,
                        "profile": {
                            "timestamp": 1618285360,
                            "is_hidden": false,
                            "height": 14972,
                            "username": "clayoglesby",
                            "description": "🐾 NFT Projects: @cloutpups, @Rebel5, @cloutagotchi, & @soookies\n🧑🏻‍💻 Product Designer in Fintech",
                            "avatar_url": "https://overdeso.com/media/avatar/ahu3LMBaBjo",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 55663042965,
                            "locked": 195190407030,
                            "watermark": 70852721372,
                            "price": 3506642767
                        }
                    },
                    "buyer": {
                        "height": 8385,
                        "pubkey": "BC1YLi3oWGPgn85Aq4FJCjoxS2gjG3d5jQUXmhceiCRiDd6byJ53Qhg",
                        "balance": 4980700155,
                        "timestamp": 1616284491,
                        "profile": {
                            "timestamp": 1616284978,
                            "is_hidden": false,
                            "height": 8385,
                            "username": "100",
                            "description": "DeSo Ideator | Putting 100% into everything I do. \n💯 Community Moderator @DeSo\n\n@spookies 212 | @chixels 08\nMy beautiful collection of DeSo NFTs @100sNFT.",
                            "avatar_url": "https://overdeso.com/media/avatar/biFsTu4gVgM",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 52798483065,
                            "locked": 147243602936,
                            "watermark": 74340771499,
                            "price": 2788784722
                        }
                    },
                    "seller": {
                        "height": 14973,
                        "pubkey": "BC1YLgzcfyi5GZoMb9xoVzDCMy9KEzzvTqoJzRrVDfhWE2FfFubxaVm",
                        "balance": 194658476187,
                        "timestamp": 1618285360,
                        "profile": {
                            "timestamp": 1618285360,
                            "is_hidden": false,
                            "height": 14972,
                            "username": "clayoglesby",
                            "description": "🐾 NFT Projects: @cloutpups, @Rebel5, @cloutagotchi, & @soookies\n🧑🏻‍💻 Product Designer in Fintech",
                            "avatar_url": "https://overdeso.com/media/avatar/ahu3LMBaBjo",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 55663042965,
                            "locked": 195190407030,
                            "watermark": 70852721372,
                            "price": 3506642767
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
