---
description: Post related API methods.
---

# Post

### post.get

Fetch post by its hash and optionally fetch related comments to it.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr></tbody></table>

#### Response

The method returns post information and related comments to it if requested

**author** – information about account who created that post.

**parent** - post structure of parent post if have.

**root** - post structure of root post if have.

**post** - information about requested post.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"post.get", "params": {"hash":"75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4"}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "author": {
                "coin": {
                    "locked": 9832837743208,
                    "price": 45897193951,
                    "supply": 214236141617,
                    "watermark": 217102791922
                },
                "height": 6042,
                "profile": {
                    "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8uJLGhu",
                    "description": "\ud83d\udc8e\ud83d\ude4c",
                    "height": 6044,
                    "is_hidden": 0,
                    "reward_points": 0,
                    "stake_points": 12500,
                    "username": "diamondhands"
                },
                "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                "stat": {
                    "coin_buy_count": 3,
                    "coin_buy_value": 2138017524,
                    "coin_sell_count": 2,
                    "coin_sell_value": 60683183,
                    "comment_count": 30,
                    "follower_count": 1056,
                    "following_count": 0,
                    "holder_count": 388,
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
                    "post_count": 7,
                    "quote_count": 0,
                    "receiver_coin_count": 0,
                    "receiver_coin_value": 0,
                    "receiver_connection_count": 3446,
                    "receiver_connection_value": 27896076092882,
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
                    "tx_count": 2138
                }
            },
            "parent": null,
            "post": {
                "depth": 0,
                "has_image": false,
                "has_media": false,
                "has_video": false,
                "hash": "75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4",
                "is_hidden": false,
                "is_quoted": false,
                "lang": "en",
                "media": {
                    "image_urls": []
                },
                "nft": null,
                "stat": {
                    "comment_count": 5,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "like_count": 51,
                    "quote_count": 0,
                    "repost_count": 0
                },
                "submitted_at": 1615575232,
                "text": "In retrospect, it was inevitable"
            },
            "root": null
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.list

Return list of posts for account or comments for hash depending what we passed to this method.

The method requires to pass ONE of required params.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>username</td><td></td><td>true</td><td>Username to fetch account for</td></tr><tr><td>lang</td><td></td><td>false</td><td>Languge code to fetch. Default is null so means any language</td></tr><tr><td>depth</td><td></td><td>false</td><td>Max depth to fetch. Default is null</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns related posts to account or original post hash.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.list", "params": {"hash":"75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4", "lang": "en", "offset": 0, "limit": 5}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "account": {
                    "coin": {
                        "locked": 393977,
                        "price": 537420,
                        "supply": 733089131,
                        "watermark": 2301116921
                    },
                    "height": 7660,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/asXKScybCfH",
                        "description": "Recovering at home. Thanks for the support. ",
                        "height": 7660,
                        "is_hidden": 0,
                        "reward_points": 100,
                        "stake_points": 12500,
                        "username": "Tiger_Woods"
                    },
                    "pubkey": "BC1YLgUsQ4PqaFet9AA9P4DmoczYmmwwHhpCrddgQXNarjDtnoddUEa",
                    "stat": {
                        "coin_buy_count": 1,
                        "coin_buy_value": 4061001,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "comment_count": 30,
                        "follower_count": 1,
                        "following_count": 0,
                        "holder_count": 1,
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
                        "post_count": 4,
                        "quote_count": 0,
                        "receiver_coin_count": 0,
                        "receiver_coin_value": 0,
                        "receiver_connection_count": 7,
                        "receiver_connection_value": 19914534,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 0,
                        "receiver_seed_value": 0,
                        "repost_count": 0,
                        "reward_coins": 442264248,
                        "reward_value": 4268387,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 1,
                        "sender_connection_value": 0,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 44
                    }
                },
                "post": {
                    "depth": 1,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "hash": "670bb56427469e5b688404e5bc984a6fdc1ddc11232a3516bbeb9ba366ced93a",
                    "is_hidden": false,
                    "is_quoted": false,
                    "lang": "en",
                    "media": null,
                    "nft": null,
                    "stat": {
                        "comment_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "like_count": 0,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616029421,
                    "text": "In retrospect, I shouldn\u2019t have used self driving mode. "
                }
            },
            {
                "account": {
                    "coin": {
                        "locked": 158231166,
                        "price": 29254639,
                        "supply": 5408754548,
                        "watermark": 7664826343
                    },
                    "height": 7660,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/h4UCxSSHQm5",
                        "description": "",
                        "height": 7927,
                        "is_hidden": 0,
                        "reward_points": 3000,
                        "stake_points": 12500,
                        "username": "0x000"
                    },
                    "pubkey": "BC1YLhVom6B4dVcKrFJyBPz3kJrDonHDp415uc1mVUbU4HtTj9LM5wA",
                    "stat": {
                        "coin_buy_count": 4,
                        "coin_buy_value": 7322107328,
                        "coin_sell_count": 2,
                        "coin_sell_value": 3649267231,
                        "comment_count": 2,
                        "follower_count": 26,
                        "following_count": 3,
                        "holder_count": 3,
                        "holding_count": 3,
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
                        "post_count": 4,
                        "quote_count": 0,
                        "receiver_coin_count": 0,
                        "receiver_coin_value": 0,
                        "receiver_connection_count": 48,
                        "receiver_connection_value": 1129147178,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 0,
                        "receiver_seed_value": 0,
                        "repost_count": 0,
                        "reward_coins": 1140489646,
                        "reward_value": 136655235,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 1,
                        "sender_connection_value": 1877707331,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 54
                    }
                },
                "post": {
                    "depth": 1,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "hash": "0032655f6921ea9d2bddbdad31c185de888d61465f7d5a19f0cef26b53c36e35",
                    "is_hidden": false,
                    "is_quoted": false,
                    "lang": "en",
                    "media": null,
                    "nft": null,
                    "stat": {
                        "comment_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "like_count": 0,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616136381,
                    "text": "How do we sell bitclout back to btc?"
                }
            },
            {
                "account": {
                    "coin": {
                        "locked": 9203047835,
                        "price": 439158443,
                        "supply": 20956099015,
                        "watermark": 22155949113
                    },
                    "height": 7497,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/gjDetZZjoSw",
                        "description": " ",
                        "height": 7653,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "empowering_"
                    },
                    "pubkey": "BC1YLgGpBTw2Qb59LmZSzsKjgEDvcnSX6oKw2EpmdZjgG8KNU96n738",
                    "stat": {
                        "coin_buy_count": 108,
                        "coin_buy_value": 99807912348,
                        "coin_sell_count": 10,
                        "coin_sell_value": 8216841420,
                        "comment_count": 130,
                        "follower_count": 228,
                        "following_count": 545,
                        "holder_count": 24,
                        "holding_count": 82,
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
                        "post_count": 51,
                        "quote_count": 0,
                        "receiver_coin_count": 0,
                        "receiver_coin_value": 0,
                        "receiver_connection_count": 568,
                        "receiver_connection_value": 11844933116,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 1,
                        "receiver_seed_value": 50000000,
                        "repost_count": 0,
                        "reward_coins": 1913403604,
                        "reward_value": 1079964602,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 2,
                        "sender_connection_value": 1489065652,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 1874
                    }
                },
                "post": {
                    "depth": 1,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "hash": "fe490b6aa0479fa871eb8badc55d60ecd1fc757834cb307dd2ee1d5dee55c31f",
                    "is_hidden": false,
                    "is_quoted": false,
                    "lang": "en",
                    "media": null,
                    "nft": null,
                    "stat": {
                        "comment_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "like_count": 0,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616149382,
                    "text": "It really was"
                }
            },
            {
                "account": {
                    "coin": {
                        "locked": 597283130028,
                        "price": 7092298589,
                        "supply": 84215733802,
                        "watermark": 85407409619
                    },
                    "height": 8079,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/PAhcirRaxiT",
                        "description": "I am the Diamond Stallion (\ud83d\udc8e\ud83d\udc0e) of BitClout and the Golden Gate bridge (\ud83c\udf09\u2728) between the NFT and the mainstream world. Investing in me is investing in the digital revolution.",
                        "height": 8079,
                        "is_hidden": 0,
                        "reward_points": 1500,
                        "stake_points": 12500,
                        "username": "farokh"
                    },
                    "pubkey": "BC1YLjAHiSa7xRsFC7wVp46usEidw8no1ugyKLfGgtvz4YqFofSGvHk",
                    "stat": {
                        "coin_buy_count": 9,
                        "coin_buy_value": 41182585108,
                        "coin_sell_count": 6,
                        "coin_sell_value": 23758932988,
                        "comment_count": 59,
                        "follower_count": 299,
                        "following_count": 19,
                        "holder_count": 114,
                        "holding_count": 5,
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
                        "post_count": 32,
                        "quote_count": 0,
                        "receiver_coin_count": 0,
                        "receiver_coin_value": 0,
                        "receiver_connection_count": 1160,
                        "receiver_connection_value": 765622300474,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 1,
                        "receiver_seed_value": 50000000,
                        "repost_count": 0,
                        "reward_coins": 9064942312,
                        "reward_value": 96259813630,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 2,
                        "sender_connection_value": 10299651718,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 801
                    }
                },
                "post": {
                    "depth": 1,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "hash": "23c768e6c328a95d3ecdd9d2fd1297bf011cade03b3517f8d8c3dfa855825a2c",
                    "is_hidden": false,
                    "is_quoted": false,
                    "lang": "en",
                    "media": null,
                    "nft": null,
                    "stat": {
                        "comment_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "like_count": 0,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616392631,
                    "text": "HAD TO HAPPEN."
                }
            },
            {
                "account": {
                    "coin": {
                        "locked": 11144250519,
                        "price": 498923581,
                        "supply": 22336588058,
                        "watermark": 22336588058
                    },
                    "height": 9085,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/SLoDCNgKCRD",
                        "description": "Forbes 80 Under 80. Meme dealer. Working on new things. Formerly found at @a16z, @GoldmanSachs, @Mubadala.",
                        "height": 9085,
                        "is_hidden": 0,
                        "reward_points": 5000,
                        "stake_points": 12500,
                        "username": "anamostarac"
                    },
                    "pubkey": "BC1YLgJxoT1oDhZneT5Gy6rbWDVaGmpxRW7u29e3cXcAaryFXai31F2",
                    "stat": {
                        "coin_buy_count": 0,
                        "coin_buy_value": 0,
                        "coin_sell_count": 0,
                        "coin_sell_value": 0,
                        "comment_count": 7,
                        "follower_count": 34,
                        "following_count": 111,
                        "holder_count": 8,
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
                        "receiver_connection_count": 57,
                        "receiver_connection_value": 11195365058,
                        "receiver_diamond_count": 0,
                        "receiver_diamond_value": 0,
                        "receiver_seed_count": 1,
                        "receiver_seed_value": 50000000,
                        "repost_count": 0,
                        "reward_coins": 2239834805,
                        "reward_value": 2660962063,
                        "sender_coin_count": 0,
                        "sender_coin_value": 0,
                        "sender_connection_count": 2,
                        "sender_connection_value": 0,
                        "sender_diamond_count": 0,
                        "sender_diamond_value": 0,
                        "sender_seed_count": 0,
                        "sender_seed_value": 0,
                        "tx_count": 229
                    }
                },
                "post": {
                    "depth": 1,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "hash": "bd0dbfc1f231d26ec19a24e0c0b7d2189bb395fa3ebd063480a16665b019c522",
                    "is_hidden": false,
                    "is_quoted": false,
                    "lang": "en",
                    "media": null,
                    "nft": null,
                    "stat": {
                        "comment_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "like_count": 0,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616499759,
                    "text": "I want this framed "
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}
