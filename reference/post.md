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
                "account": {
                    "balance": 26676665293,
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                },
                "coin": {
                    "locked": 5710186658419,
                    "price": 31947270018,
                    "supply": 178737859453,
                    "watermark": 255810788786
                },
                "profile": {
                    "avatar_url": "https://overdeso.com/media/avatar/Xs8Q5JRbC7m",
                    "description": "\ud83d\udc8e\ud83d\ude4c",
                    "height": 6044,
                    "is_hidden": 0,
                    "reward_points": 0,
                    "stake_points": 12500,
                    "username": "diamondhands"
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
                "is_nft": false,
                "is_quoted": false,
                "lang": "en",
                "media": {
                    "image_urls": []
                },
                "nft": null,
                "stat": {
                    "comment_count": 49,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "like_count": 190,
                    "quote_count": 7,
                    "repost_count": 13
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
                    "account": {
                        "height": 7660,
                        "pubkey": "BC1YLgUsQ4PqaFet9AA9P4DmoczYmmwwHhpCrddgQXNarjDtnoddUEa"
                    },
                    "coin": {
                        "locked": 393977,
                        "price": 537420,
                        "supply": 733089131,
                        "watermark": 2301116921
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/asXKScybCfH",
                        "description": "Recovering at home. Thanks for the support. ",
                        "height": 7660,
                        "is_hidden": 0,
                        "reward_points": 100,
                        "stake_points": 12500,
                        "username": "Tiger_Woods"
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
                    "account": {
                        "height": 7660,
                        "pubkey": "BC1YLhVom6B4dVcKrFJyBPz3kJrDonHDp415uc1mVUbU4HtTj9LM5wA"
                    },
                    "coin": {
                        "locked": 229832204,
                        "price": 37520964,
                        "supply": 6125434271,
                        "watermark": 7664826343
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/h4UCxSSHQm5",
                        "description": "",
                        "height": 7927,
                        "is_hidden": 0,
                        "reward_points": 3000,
                        "stake_points": 12500,
                        "username": "MoonCat"
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
                        "diamond_count": 1,
                        "diamond_value": 52487,
                        "like_count": 5,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616136381,
                    "text": "How do we sell bitclout back to btc?"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 7497,
                        "pubkey": "BC1YLgGpBTw2Qb59LmZSzsKjgEDvcnSX6oKw2EpmdZjgG8KNU96n738"
                    },
                    "coin": {
                        "locked": 1834490345,
                        "price": 149857005,
                        "supply": 12241605540,
                        "watermark": 22379306389
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/gjDetZZjoSw",
                        "description": " ",
                        "height": 7653,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "empowering_"
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
                        "diamond_count": 1,
                        "diamond_value": 52491,
                        "like_count": 1,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616149382,
                    "text": "It really was"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 8079,
                        "pubkey": "BC1YLjAHiSa7xRsFC7wVp46usEidw8no1ugyKLfGgtvz4YqFofSGvHk"
                    },
                    "coin": {
                        "locked": 884071716625,
                        "price": 9211390292,
                        "supply": 95975926385,
                        "watermark": 155743945147
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/PAhcirRaxiT",
                        "description": "I am the Diamond Stallion (\ud83d\udc8e\ud83d\udc0e) of BitClout and the Golden Gate bridge (\ud83c\udf09\u2728) between the NFT and the mainstream world. Investing in me is investing in the digital revolution.",
                        "height": 8079,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "farokh"
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
                        "comment_count": 1,
                        "diamond_count": 1,
                        "diamond_value": 52491,
                        "like_count": 4,
                        "quote_count": 0,
                        "repost_count": 0
                    },
                    "submitted_at": 1616392631,
                    "text": "HAD TO HAPPEN."
                }
            },
            {
                "account": {
                    "account": {
                        "height": 9085,
                        "pubkey": "BC1YLgJxoT1oDhZneT5Gy6rbWDVaGmpxRW7u29e3cXcAaryFXai31F2"
                    },
                    "coin": {
                        "locked": 1331566877,
                        "price": 121034379,
                        "supply": 11001559124,
                        "watermark": 26144349733
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/SLoDCNgKCRD",
                        "description": "Forbes 80 Under 80. Meme dealer. Working on new things. Formerly found at @a16z, @GoldmanSachs, @Mubadala.",
                        "height": 9085,
                        "is_hidden": 0,
                        "reward_points": 5000,
                        "stake_points": 12500,
                        "username": "anamostarac"
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
                        "comment_count": 1,
                        "diamond_count": 1,
                        "diamond_value": 52487,
                        "like_count": 3,
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

### post.like.list

Get post likes or likes of posts for account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Account public key</td></tr><tr><td>username</td><td></td><td>true</td><td>Account username</td></tr></tbody></table>

#### Response

The method returned likes in chronological order for post or for account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.like.list", "params": {"hash":"75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "account": {
                    "account": {
                        "height": 5876,
                        "pubkey": "BC1YLhrqTukBnBZ6pU4v4cwbNrsXp8VLdZ3wNw8r9SBhQieAnX6VtWW"
                    },
                    "coin": null,
                    "profile": null
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 4819,
                        "pubkey": "BC1YLhbeXFZYNh22ktvNJqSbpfTkV7aq5gBLbkG6h9AnD1XxEPvpuoa"
                    },
                    "coin": {
                        "locked": 3627958770,
                        "price": 236106712,
                        "supply": 15365758716,
                        "watermark": 28434180030
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/VX7zZ8PY4f9",
                        "description": "",
                        "height": 6059,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "btcpepe"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 4323,
                        "pubkey": "BC1YLitP6QBiJ8TAPGDH3ZdGBavRuXterrL3cYwVgu1FqqmQz6d71Ga"
                    },
                    "coin": {
                        "locked": 28401911,
                        "price": 9308901,
                        "supply": 3051048758,
                        "watermark": 3140592217
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/TgNPvpcj14T",
                        "description": "",
                        "height": 7659,
                        "is_hidden": 0,
                        "reward_points": 1500,
                        "stake_points": 12500,
                        "username": "tienne_e"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 3918,
                        "pubkey": "BC1YLjVVDGqjkAg7ZrzonH8tBk1LHKSfaUtpxbSUVa9ttToM8JRJzmy"
                    },
                    "coin": {
                        "locked": 5131608172,
                        "price": 297510595,
                        "supply": 17248488820,
                        "watermark": 36938030418
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/UBjoE4rG32X",
                        "description": "Frontier Technology investor. Care deeply about free speech and evolving the internet beyond ad based revenue models. Work hard, be kind. ",
                        "height": 7652,
                        "is_hidden": 0,
                        "reward_points": 500,
                        "stake_points": 12500,
                        "username": "Atticus"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 0,
                        "pubkey": "BC1YLh6hhf2koahaMb5nydvB5EHzEAP6MZPSsQM8Ka4Ko4gjbeXjQjB"
                    },
                    "coin": {
                        "locked": 33460153752,
                        "price": 1038369903,
                        "supply": 32223732256,
                        "watermark": 63928860658
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/QLRLYNDP8f1",
                        "description": "Decentralize",
                        "height": 7663,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "ayo"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 4646,
                        "pubkey": "BC1YLinotRvfP6fzs5a3HPDABsMYhTVv17c22g81FHAkoeytJBxfXT7"
                    },
                    "coin": {
                        "locked": 948872645,
                        "price": 96561803,
                        "supply": 9826583677,
                        "watermark": 13302771075
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/fZA9kDCGzbh",
                        "description": "Sapere aude \n\nwww.wrapbook.com",
                        "height": 7652,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "cameronwoodward"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 2497,
                        "pubkey": "BC1YLi6LpXTemAG8T9ptyWAkMywrjynwZcKjB5DkDXxrsG5kgAwAqxq"
                    },
                    "coin": {
                        "locked": 1179056963140,
                        "price": 11160664430,
                        "supply": 105643975808,
                        "watermark": 192232015512
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/QLa8TR7Mxby",
                        "description": "buidling bitclout",
                        "height": 2498,
                        "is_hidden": 0,
                        "reward_points": 200,
                        "stake_points": 12500,
                        "username": "maebeam"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 5553,
                        "pubkey": "BC1YLidMuCokb3d2e8D725J22J7puc5vN38aDLntjaww1JT7jZGKaGF"
                    },
                    "coin": {
                        "locked": 34890658666,
                        "price": 1067758201,
                        "supply": 32676554116,
                        "watermark": 68227071880
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ciPWWVNfeeK",
                        "description": "Entrepreneur, Woman, Co-Founder Bancor, Decentralist, New Economist, Plant Lover",
                        "height": 6381,
                        "is_hidden": 0,
                        "reward_points": 1000,
                        "stake_points": 12500,
                        "username": "GaliaB"
                    }
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 6047,
                        "pubkey": "BC1YLieN6iiss8hC7mo8y9gtr2bbW1336SkHEUTuWnVgaqrq64Sf3rz"
                    },
                    "coin": null,
                    "profile": null
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            },
            {
                "account": {
                    "account": {
                        "height": 0,
                        "pubkey": "BC1YLi7qauajrATCFtftpb2SvRBaBeMwBJLGszf49ns31ErWTbUhtNY"
                    },
                    "coin": null,
                    "profile": null
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615575232,
                    "text": "In retrospect, it was inevitable"
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.diamond.list

Fetch diamond list for post hash or account as receiver or sender.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>username</td><td></td><td>true</td><td>Username to fetch account for</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns structure as list each on with keys:

* **diamond** – contains level only of diamond;
* **post** – related post information;
* **sender** – information about sender account;
* **receiver** – information about receiver account.

If no diamonds found returned empty array list there was no error.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.diamond.list", "params": {"username": "diamondhands"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "diamond": {
                    "level": 6,
                    "value": 5000000000
                },
                "post": {
                    "account": {
                        "height": 6055,
                        "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8"
                    },
                    "coin": {
                        "locked": 2459499208919,
                        "price": 18220683927,
                        "supply": 134983912720,
                        "watermark": 166627229450
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsYUFsRZEjH",
                        "description": "The Community Builder \ud83d\udc4f\n\n@GiftClout\ud83d\udc9d\n@VerifiedProfile\u2705\n\ud83d\ude4f JUST HODL @frbuyback & @socialtrustfund \ud83d\ude4f \n\nDay 21 of 60 \ud83d\ude80 to the \ud83c\udf1d",
                        "height": 6062,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "RajLahoti"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 6055,
                        "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8"
                    },
                    "coin": {
                        "locked": 2459499208919,
                        "price": 18220683927,
                        "supply": 134983912720,
                        "watermark": 166627229450
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsYUFsRZEjH",
                        "description": "The Community Builder \ud83d\udc4f\n\n@GiftClout\ud83d\udc9d\n@VerifiedProfile\u2705\n\ud83d\ude4f JUST HODL @frbuyback & @socialtrustfund \ud83d\ude4f \n\nDay 21 of 60 \ud83d\ude80 to the \ud83c\udf1d",
                        "height": 6062,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "RajLahoti"
                    }
                }
            },
            {
                "diamond": {
                    "level": 6,
                    "value": 5000000000
                },
                "post": {
                    "account": {
                        "height": 9768,
                        "pubkey": "BC1YLhKYCXfy2tguomfrydUAEFcf5ANqkaQELWgTHWVVNPB3UHibxth"
                    },
                    "coin": {
                        "locked": 77812301643,
                        "price": 1822632011,
                        "supply": 42692272026,
                        "watermark": 66920220515
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Rg4vBr8mzKZ",
                        "description": "\u2705 Official @GiftClout\ud83d\udc9d | We send new creators \uff0411.11 of \ud83d\udcb2clout to get them started on their journey \ud83d\ude4f\ud83c\udffd\n\n33.33% FR \n> 1/2 supporting new users\n> 1/2 re-invested into our coin",
                        "height": 9776,
                        "is_hidden": 0,
                        "reward_points": 3333,
                        "stake_points": 12500,
                        "username": "GiftClout"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 9768,
                        "pubkey": "BC1YLhKYCXfy2tguomfrydUAEFcf5ANqkaQELWgTHWVVNPB3UHibxth"
                    },
                    "coin": {
                        "locked": 77812301643,
                        "price": 1822632011,
                        "supply": 42692272026,
                        "watermark": 66920220515
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Rg4vBr8mzKZ",
                        "description": "\u2705 Official @GiftClout\ud83d\udc9d | We send new creators \uff0411.11 of \ud83d\udcb2clout to get them started on their journey \ud83d\ude4f\ud83c\udffd\n\n33.33% FR \n> 1/2 supporting new users\n> 1/2 re-invested into our coin",
                        "height": 9776,
                        "is_hidden": 0,
                        "reward_points": 3333,
                        "stake_points": 12500,
                        "username": "GiftClout"
                    }
                }
            },
            {
                "diamond": {
                    "level": 1,
                    "value": 50000
                },
                "post": {
                    "account": {
                        "height": 6557,
                        "pubkey": "BC1YLiKy1qBAXKCxVk3akggiaU2atz7upTCa1WyW3ViWp4Q46KxfftZ"
                    },
                    "coin": {
                        "locked": 14588009793,
                        "price": 597031840,
                        "supply": 24434224128,
                        "watermark": 38438992674
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsWGqbjBrnb",
                        "description": "Value BitClout Investor.\nFrom \ud83c\udde8\ud83c\udded\nI will give away a one-way ticket to Antarctica among my subscribers \u2708\ufe0f\np.s. Sorry for my awful english.",
                        "height": 7655,
                        "is_hidden": 0,
                        "reward_points": 1100,
                        "stake_points": 12500,
                        "username": "pingu_venture"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 6557,
                        "pubkey": "BC1YLiKy1qBAXKCxVk3akggiaU2atz7upTCa1WyW3ViWp4Q46KxfftZ"
                    },
                    "coin": {
                        "locked": 14588009793,
                        "price": 597031840,
                        "supply": 24434224128,
                        "watermark": 38438992674
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsWGqbjBrnb",
                        "description": "Value BitClout Investor.\nFrom \ud83c\udde8\ud83c\udded\nI will give away a one-way ticket to Antarctica among my subscribers \u2708\ufe0f\np.s. Sorry for my awful english.",
                        "height": 7655,
                        "is_hidden": 0,
                        "reward_points": 1100,
                        "stake_points": 12500,
                        "username": "pingu_venture"
                    }
                }
            },
            {
                "diamond": {
                    "level": 1,
                    "value": 50000
                },
                "post": {
                    "account": {
                        "height": 9977,
                        "pubkey": "BC1YLga4HDxYaQbcSUJpg5dNqe5Mv4a9qKSxS3K28kLFT7ERse7yUcq"
                    },
                    "coin": {
                        "locked": 6574120736,
                        "price": 350933828,
                        "supply": 18733220353,
                        "watermark": 24568140092
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/RLfZySCbu1y",
                        "description": "GMBAds\u269c\ufe0fMarketing \nTorts Law Start-Up\u2696\ufe0f\nDad\ud83d\udc68\u200d\ud83d\udc66\u2693\ufe0f\n\u041e\u0434\u0435\u0441\u0441\u0430 \ud83c\uddfa\ud83c\udde6\ud83d\udccdNew York\ud83d\uddfd\nAds Soho BitClout Art NFT House \ud83d\udc8e\ud83e\udd32\ud83d\udd79\n11%FR\nBit All Day Clout All Night @BitCloutLabs",
                        "height": 9979,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "GeneGMB"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 9977,
                        "pubkey": "BC1YLga4HDxYaQbcSUJpg5dNqe5Mv4a9qKSxS3K28kLFT7ERse7yUcq"
                    },
                    "coin": {
                        "locked": 6574120736,
                        "price": 350933828,
                        "supply": 18733220353,
                        "watermark": 24568140092
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/RLfZySCbu1y",
                        "description": "GMBAds\u269c\ufe0fMarketing \nTorts Law Start-Up\u2696\ufe0f\nDad\ud83d\udc68\u200d\ud83d\udc66\u2693\ufe0f\n\u041e\u0434\u0435\u0441\u0441\u0430 \ud83c\uddfa\ud83c\udde6\ud83d\udccdNew York\ud83d\uddfd\nAds Soho BitClout Art NFT House \ud83d\udc8e\ud83e\udd32\ud83d\udd79\n11%FR\nBit All Day Clout All Night @BitCloutLabs",
                        "height": 9979,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "GeneGMB"
                    }
                }
            },
            {
                "diamond": {
                    "level": 1,
                    "value": 50000
                },
                "post": {
                    "account": {
                        "height": 10081,
                        "pubkey": "BC1YLgdWqLHmMH4iuGsdGnC1xXUUSNNqRqwPLpVNC14GxQDQp9DUuyf"
                    },
                    "coin": {
                        "locked": 1068357607,
                        "price": 104506794,
                        "supply": 10222853107,
                        "watermark": 13438450504
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/WgzVxiV14ab",
                        "description": "Keeping it pure. Asker of good questions. Finder of beautiful and sometimes hilarious things. Examiner of life up close and from unusual angles. 8% founder's fee. \u267e",
                        "height": 10082,
                        "is_hidden": 0,
                        "reward_points": 800,
                        "stake_points": 12500,
                        "username": "Fireweed"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 10081,
                        "pubkey": "BC1YLgdWqLHmMH4iuGsdGnC1xXUUSNNqRqwPLpVNC14GxQDQp9DUuyf"
                    },
                    "coin": {
                        "locked": 1068357607,
                        "price": 104506794,
                        "supply": 10222853107,
                        "watermark": 13438450504
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/WgzVxiV14ab",
                        "description": "Keeping it pure. Asker of good questions. Finder of beautiful and sometimes hilarious things. Examiner of life up close and from unusual angles. 8% founder's fee. \u267e",
                        "height": 10082,
                        "is_hidden": 0,
                        "reward_points": 800,
                        "stake_points": 12500,
                        "username": "Fireweed"
                    }
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.stat.list

Get post historical statistics

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format.</td></tr><tr><td>period</td><td></td><td>false</td><td>Aggregation period. One of: hour, day, month. Default is hour</td></tr><tr><td>start_at</td><td></td><td>false</td><td>Timestamp to start our lookup. Default is 1610948544 that is genesis block timestamp. That means we fetch from first stat record.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns statistic related data in chronological order (low to high).

**count** – contains current resulting datataset in response not total count of data we have.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.stat.list", "params": {"hash":"1b50b5bf8bf7190d60f938443f825de447b01ee865a96b08e1ae5461ad4b5c24", "period": "hour", "start_at": 1618891732, "limit": 5}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 5,
            "list": [
                {
                    "comment_count": "0",
                    "diamond_count": "0",
                    "diamond_value": "0",
                    "like_count": "0",
                    "quote_count": "0",
                    "repost_count": "0",
                    "ts": 1618884000
                },
                {
                    "comment_count": "0",
                    "diamond_count": "0",
                    "diamond_value": "0",
                    "like_count": "0",
                    "quote_count": "0",
                    "repost_count": "0",
                    "ts": 1618887600
                },
                {
                    "comment_count": 15,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "like_count": 26,
                    "quote_count": 0,
                    "repost_count": 3,
                    "ts": 1618891200
                },
                {
                    "comment_count": 41,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "like_count": 43,
                    "quote_count": 1,
                    "repost_count": 5,
                    "ts": 1618894800
                },
                {
                    "comment_count": 47,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "like_count": 45,
                    "quote_count": 1,
                    "repost_count": 6,
                    "ts": 1618898400
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

