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
            "is_burned": true,
            "is_pending": false,
            "is_selling": false,
            "last_accepted_bid": 0,
            "min_bid": 0,
            "serial": 3
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
 curl -s --data '[{"method":"nft.list", "params": {"hash": "902018d6de32fb3f4f578fb53aa179325bd9d07fae0502279a6d0c27b01f5664", "limit": 20}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 100,
            "list": [
                {
                    "is_burned": false,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 1
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 2
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 3
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 4
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 5
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 6
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 7
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 8
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 9
                },
                {
                    "is_burned": false,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 10
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 11
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 12
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 13
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 14
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 15
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 16
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 17
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 18
                },
                {
                    "is_burned": true,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 19
                },
                {
                    "is_burned": false,
                    "is_pending": false,
                    "is_selling": false,
                    "last_accepted_bid": 0,
                    "min_bid": 0,
                    "serial": 20
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
            "count": 9223372036854775807,
            "list": [
                {
                    "account": {
                        "account": {
                            "balance": 1845482208,
                            "height": 26194,
                            "pubkey": "BC1YLhYkBAKMN4xj1iXg4CFUVPZmC2REdn7NC1qYm9ryc5jGbnsbkD3"
                        },
                        "coin": {
                            "locked": 7586949031,
                            "price": 393960196,
                            "supply": 19258161353,
                            "watermark": 31439231520
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/bNfY24sthMe",
                            "description": "Artist - making pretty things\n\ud83e\udd16 Creator: @CloBits \ud83e\udd16\n\ud83d\udc68\u200d\ud83d\udcbb Former startup guy. Did data+design projects for Google, Lego, Gatorade, Microsoft\n\ud83e\udeb2 My other weird art @BugAndGlass \ud83e\udeb2",
                            "height": 26206,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "JoshuaCottrell"
                        }
                    },
                    "bid": {
                        "serial": 1,
                        "value": 1260000000
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 952130016,
                            "height": 10760,
                            "pubkey": "BC1YLiUx62yxSzxnR79WnkdJKkD7AYqdUpDjg5yxztDB954wmbTjpr7"
                        },
                        "coin": {
                            "locked": 7669029655,
                            "price": 390162247,
                            "supply": 19656001336,
                            "watermark": 39738751954
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/SWaH8FpQRMN",
                            "description": "The Goat\ud83d\udc10 \n| @Creatorfundmanager |\n| @GoatInvesting |\n\n",
                            "height": 10836,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "GoatTrade"
                        }
                    },
                    "bid": {
                        "serial": 1,
                        "value": 1194571865
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 1335676369,
                            "height": 9987,
                            "pubkey": "BC1YLghsEY1pn9KbMght9P31nz5nZHoEcdVUyDSLhvX4Cm2j6xBZocp"
                        },
                        "coin": {
                            "locked": 27107721914,
                            "price": 903526358,
                            "supply": 30002137342,
                            "watermark": 38590247207
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/hZaE6JiRzdi",
                            "description": "TO-based IT Recruiter\n\u30fe(\uff3e\u3002^*)\u266a\uff5e\n\n@DeSoRecruiter @DeSoTalent\n@zopel_memes \ud83d\ude02\ud83d\ude2d @zopel_music \ud83c\udfb5\ud83d\udd25\nhttps://zopelvault.nftz.zone/forsale\noncyber.io/zopel\nNFTs @zopelVault \ud83d\udcb0\ud83d\udd12",
                            "height": 10015,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "zopel"
                        }
                    },
                    "bid": {
                        "serial": 1,
                        "value": 173997100
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 10019202974,
                            "height": 10041,
                            "pubkey": "BC1YLj83BYpTBpx8ZthgYLkcLEkoSmykc6KL5CiDRbmkLtMThSdEvRe"
                        },
                        "coin": {
                            "locked": 23093877685,
                            "price": 822571803,
                            "supply": 28075211910,
                            "watermark": 35512011416
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/QW3cZDmxcMz",
                            "description": "DeSo Princess \ud83d\udc8e\ud83d\udc78 @cloutpunk #489 @soookies 13 @RowdyReptilians 121 @fuckeduppunks 33\nCommunity \ud83d\udc81\u200d\u2640\ufe0f love \u2665\ufe0f memes \ud83e\udda7\nannasolod.com\ud83e\ude86\n@DeSoVoices @NestingDolls @chestreshka",
                            "height": 10041,
                            "is_hidden": 0,
                            "reward_points": 1111,
                            "stake_points": 12500,
                            "username": "Matreshka"
                        }
                    },
                    "bid": {
                        "serial": 1,
                        "value": 93475415
                    }
                },
                {
                    "account": {
                        "account": {
                            "balance": 1460942369,
                            "height": 21047,
                            "pubkey": "BC1YLipvYrrhymShy1RV76qRNM26ZjX8mz3mzXRFJFKLxF5DgKANNHP"
                        },
                        "coin": {
                            "locked": 13932904289,
                            "price": 579021328,
                            "supply": 24062851588,
                            "watermark": 125982021647
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/TgXBnjHP4ap",
                            "description": "New seasons brings new change! Equality demands decentralized governance, EQUINOX Launchpad is Equality\n\nhttps://equinox-launch.medium.com/\nhttps://t.me/Equinox_Community\n",
                            "height": 21047,
                            "is_hidden": 0,
                            "reward_points": 2500,
                            "stake_points": 12500,
                            "username": "Equin0x"
                        }
                    },
                    "bid": {
                        "serial": 1,
                        "value": 66896024
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
                    "account": {
                        "account": {
                            "balance": 311870132553,
                            "height": 14973,
                            "pubkey": "BC1YLgzcfyi5GZoMb9xoVzDCMy9KEzzvTqoJzRrVDfhWE2FfFubxaVm"
                        },
                        "coin": {
                            "locked": 200060662614,
                            "price": 3564639567,
                            "supply": 56123672201,
                            "watermark": 70852721372
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/ahu3VsCGbJU",
                            "description": "\ud83d\udc3e NFT Projects:\u00a0@cloutpups,\u00a0@Rebel5,\u00a0@cloutagotchi, & @soookies\n\ud83e\uddd1\ud83c\udffb\u200d\ud83d\udcbb Product Designer in Fintech",
                            "height": 14973,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "clayoglesby"
                        }
                    },
                    "buyer": {
                        "account": {
                            "balance": 6849641375,
                            "height": 8385,
                            "pubkey": "BC1YLi3oWGPgn85Aq4FJCjoxS2gjG3d5jQUXmhceiCRiDd6byJ53Qhg"
                        },
                        "coin": {
                            "locked": 165424315449,
                            "price": 3013863640,
                            "supply": 54887790290,
                            "watermark": 74340771499
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/biFsRBz33Rn",
                            "description": "BitClout Ideator | Putting 100% into everything I do. \n\ud83d\udcaf Community Moderator @DeSo\n\n@spookies 212 | @pixelpirates 006\n",
                            "height": 8386,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "100"
                        }
                    },
                    "nft": {
                        "is_burned": false,
                        "is_pending": false,
                        "is_selling": true,
                        "last_accepted_bid": 1261000000,
                        "min_bid": 3000000000,
                        "serial": 1
                    },
                    "seller": {
                        "account": {
                            "balance": 311870132553,
                            "height": 14973,
                            "pubkey": "BC1YLgzcfyi5GZoMb9xoVzDCMy9KEzzvTqoJzRrVDfhWE2FfFubxaVm"
                        },
                        "coin": {
                            "locked": 200060662614,
                            "price": 3564639567,
                            "supply": 56123672201,
                            "watermark": 70852721372
                        },
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/ahu3VsCGbJU",
                            "description": "\ud83d\udc3e NFT Projects:\u00a0@cloutpups,\u00a0@Rebel5,\u00a0@cloutagotchi, & @soookies\n\ud83e\uddd1\ud83c\udffb\u200d\ud83d\udcbb Product Designer in Fintech",
                            "height": 14973,
                            "is_hidden": 0,
                            "reward_points": 1000,
                            "stake_points": 12500,
                            "username": "clayoglesby"
                        }
                    },
                    "trade": {
                        "buyer_value": 1261000000,
                        "coin_value": 126100000,
                        "creator_value": 126100000,
                        "gain": 1008800000,
                        "seller_value": 1008800000
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
