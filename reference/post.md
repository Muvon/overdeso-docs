---
description: Post related API methods.
---

# 📄 Post

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
            "depth": 0,
            "is_quoted": false,
            "text": "In retrospect, it was inevitable",
            "lang": null,
            "has_media": false,
            "has_image": false,
            "has_video": false,
            "media": {
                "image_urls": []
            },
            "is_hidden": false,
            "is_nft": true,
            "submitted_at": 1615574830,
            "nft": {
                "is_selling": 1,
                "has_unlockable": 0,
                "nft_count": 1,
                "creator_royalty": 0,
                "coin_royalty": 1500
            },
            "stat": {
                "last_stat_ts": 1641223938,
                "like_count": 311,
                "diamond_count": 16721,
                "diamond_value": 20644876649,
                "repost_count": 36,
                "quote_count": 29,
                "comment_count": 87,
                "nft_bid_count": 0,
                "nft_trade_count": 0,
                "nft_burned_count": 0
            },
            "hash": "75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4",
            "root": null,
            "parent": null,
            "repost": null,
            "account": {
                "height": 6042,
                "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                "balance": 1202813160669,
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
                    "supply": 164216917444,
                    "locked": 4578658488257,
                    "watermark": 255810788786,
                    "price": 27881771010
                }
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.list

Return list of global recent post list or for account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>pubkey</td><td></td><td>false</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>username</td><td></td><td>false</td><td>Username to fetch account for</td></tr><tr><td>lang</td><td></td><td>false</td><td>Languge code to fetch. Default is null so means any language</td></tr><tr><td>depth</td><td></td><td>false</td><td>Max depth to fetch. Default is null</td></tr><tr><td>has_media</td><td></td><td>false</td><td>Fetch posts that have media only</td></tr><tr><td>has_video</td><td></td><td>false</td><td>Fetch posts that have video only</td></tr><tr><td>has_image</td><td></td><td>false</td><td>Fetch posts that have image only attached to it</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Return latest posts for network or for account if passed in request.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.list", "params": {"lang": "en", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1
```

```json
[
    [
        null,
        {
            "count": 2310116,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "🔥 13 years ago Satoshi Nakamoto created the genesis block of bitcoin\n\nIn block 0, Satoshi indicated the text from the headline of The Times: \"The Times 03 / Jan / 2009 Chancellor on brink of second bailout for banks\".\n\nThe first block generated 50 BTC. Then their price was $ 0.00. On July 17, 2010, there was a demand for cue ball and the price rose to $ 0.09.\n\nSince then, BTC has grown by 52.2 million percent 🚀\n",
                    "lang": "en",
                    "has_media": true,
                    "has_image": true,
                    "has_video": false,
                    "media": {
                        "image_urls": [
                            "https://images.deso.org/912d229bdb37432b326b175b5606d0d5d60f9935db86f73e841dcae34798b7fd.webp"
                        ]
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1641225316,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 0,
                        "like_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "hash": "e1494f2839b98effa5c74c739ce2a630a41d58f1d5886bb4feafff63ec63d524",
                    "repost": null,
                    "account": {
                        "height": 44467,
                        "pubkey": "BC1YLfovdgWCbAdkRMX7W5igjhuirVrY1zRvmd5zPVjCn5DuvcmgSQh",
                        "balance": 5799801180,
                        "timestamp": 1626850074,
                        "profile": {
                            "timestamp": 1629826298,
                            "is_hidden": false,
                            "height": 54404,
                            "username": "90Degree",
                            "description": "Your daily update on \nCrypto and NFT News",
                            "avatar_url": "https://overdeso.com/media/avatar/Vh1etMK6oXw",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 16809167440,
                            "locked": 4749402584,
                            "watermark": 19317114377,
                            "price": 282548353
                        }
                    },
                    "state": {
                        "is_liked": false,
                        "diamond_level": 0
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "some NYC #streetphotography for the @PhotographersCorner contest\n\nPosted via @cloutfeed",
                    "lang": "en",
                    "has_media": true,
                    "has_image": true,
                    "has_video": false,
                    "media": {
                        "image_urls": [
                            "https://images.deso.org/b1cb798da53da0ec567b47eb422e31171f1eef10100efa9ddb10eee075c0efc0.webp"
                        ]
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1641225316,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 0,
                        "like_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "hash": "6429bb0305462db28dba147bb3048add539abcba091aca95b35b5bbfd62b4446",
                    "repost": null,
                    "account": {
                        "height": 41364,
                        "pubkey": "BC1YLhbYNnu9wxmPuT4xmdi3sCshgU3cS1ZqzjRv8P5kpqtKBZxBnzR",
                        "balance": 323874398,
                        "timestamp": 1625921846,
                        "profile": {
                            "timestamp": 1625921846,
                            "is_hidden": false,
                            "height": 41363,
                            "username": "almostgreat",
                            "description": "home after picking up cigarettes and milk. now sharing and selling some of my old photos. \n\ncommunity at ardrive.io\n\n🛒 almostgreatco.etsy.com",
                            "avatar_url": "https://overdeso.com/media/avatar/UMB5qyP9WVP",
                            "reward_points": 2000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 9279501171,
                            "locked": 799050340,
                            "watermark": 9323560621,
                            "price": 86109191
                        }
                    },
                    "state": {
                        "is_liked": false,
                        "diamond_level": 0
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.comment.list

Get list of comments for post hash or for some account.&#x20;

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>username</td><td></td><td>true</td><td>Username to fetch account for</td></tr><tr><td>lang</td><td></td><td>false</td><td>Languge code to fetch. Default is null so means any language</td></tr><tr><td>depth</td><td></td><td>false</td><td>Max depth to fetch. Default is null</td></tr><tr><td>has_media</td><td></td><td>false</td><td>Fetch posts that have media only</td></tr><tr><td>has_video</td><td></td><td>false</td><td>Fetch posts that have video only</td></tr><tr><td>has_image</td><td></td><td>false</td><td>Fetch posts that have image only attached to it</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of comments in chronological order that represent post structure.

#### Examplees

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.comment.list", "params": {"username": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1   | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "depth": 1,
                "is_quoted": false,
                "text": "Could this be the rarest of them all? @charlie",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1635356303,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1635767361,
                    "like_count": 2,
                    "diamond_count": 1,
                    "diamond_value": 50000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 2,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "hash": "e3403e1075fb7222d3b122333a47274a67870be896ff623580a05b9a7b7f9c2a",
                "root": {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "BEHOLD MATIES!",
                    "lang": "ku",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1635356303,
                    "hash": "696c39c9023838460fa562c888381328665d3ed9c0da1ab07b8866339328783c",
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 1202813160669,
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
                            "supply": 164216917444,
                            "locked": 4578658488257,
                            "watermark": 255810788786,
                            "price": 27881771010
                        }
                    }
                },
                "parent": {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "BEHOLD MATIES!",
                    "lang": "ku",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1635356303,
                    "hash": "696c39c9023838460fa562c888381328665d3ed9c0da1ab07b8866339328783c",
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 1202813160669,
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
                            "supply": 164216917444,
                            "locked": 4578658488257,
                            "watermark": 255810788786,
                            "price": 27881771010
                        }
                    }
                },
                "account": {
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "balance": 1202813160669,
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
                        "supply": 164216917444,
                        "locked": 4578658488257,
                        "watermark": 255810788786,
                        "price": 27881771010
                    }
                },
                "state": {
                    "is_liked": false,
                    "diamond_level": 0
                }
            },
            {
                "depth": 0,
                "is_quoted": true,
                "text": "BEHOLD MATIES!",
                "lang": "ku",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1635356303,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1641159951,
                    "like_count": 273,
                    "diamond_count": 45,
                    "diamond_value": 111950000,
                    "repost_count": 2,
                    "quote_count": 3,
                    "comment_count": 30,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "hash": "696c39c9023838460fa562c888381328665d3ed9c0da1ab07b8866339328783c",
                "root": null,
                "parent": null,
                "account": {
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "balance": 1202813160669,
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
                        "supply": 164216917444,
                        "locked": 4578658488257,
                        "watermark": 255810788786,
                        "price": 27881771010
                    }
                },
                "state": {
                    "is_liked": false,
                    "diamond_level": 0
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
curl -s --data '[{"method":"post.like.list", "params": {"hash":"75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "post": {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "In retrospect, it was inevitable",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": true,
                    "submitted_at": 1615574830
                },
                "account": {
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
                    }
                }
            },
            {
                "post": {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "In retrospect, it was inevitable",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": true,
                    "submitted_at": 1615574830
                },
                "account": {
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
                    }
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
    curl -s --data '[{"method":"post.diamond.list", "params": {"username": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
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
                    "submitted_at": 1615574830,
                    "text": "In retrospect, it was inevitable"
                },
                "receiver": {
                    "balance": 1568580768648,
                    "coin": {
                        "locked": 5625110063387,
                        "price": 31982730622,
                        "supply": 175879606086,
                        "watermark": 255810788786
                    },
                    "height": 6042,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PxVxfRr8",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6043,
                        "is_hidden": false,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "timestamp": 1615574830,
                        "username": "diamondhands"
                    },
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "timestamp": 1615574505
                },
                "sender": {
                    "balance": 26709020091,
                    "coin": {
                        "locked": 1119643937314,
                        "price": 10784891159,
                        "supply": 103815970024,
                        "watermark": 166627229450
                    },
                    "height": 6055,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsYUGJvrVLC",
                        "description": "Community Builder \ud83d\udc4f on $CLOUT Ecosystem & Clubhouse\n\n// Projects //\n\n@GiftClout\ud83d\udc9d Co-founder\nBuilding/Dreaming up Gift Economy Node of $CLOUT Ecosystem\n\n@FBV\u2705 Founder & Managing Director\nInvestments into Projects aligned with a new paradigm\n\n@BitCloutUniversity\ud83c\udfeb Founder\nPlatform for Education & Empowerment onto the BitClout Platform & Ecosystem\n\n// Topics of Interest //\n\n\ud83d\udc4f Conscious Community\n\ud83c\udf81 Gift Economy\n\ud83d\udd17 Blockchain\n\ud83d\udc65 Relationships\n\ud83d\ude4f\ud83c\udffd Trust\n\ud83e\udd1d Reputation\n\ud83d\udcb8 Wealth Redistribution\n\ud83d\ude4c Philanthropy",
                        "height": 6061,
                        "is_hidden": false,
                        "reward_points": 222,
                        "stake_points": 12500,
                        "timestamp": 1615580501,
                        "username": "RajLahoti"
                    },
                    "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8",
                    "timestamp": 1615578129
                }
            },
            {
                "diamond": {
                    "level": 6,
                    "value": 5000000000
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
                    "submitted_at": 1615574830,
                    "text": "In retrospect, it was inevitable"
                },
                "receiver": {
                    "balance": 1568580768648,
                    "coin": {
                        "locked": 5625110063387,
                        "price": 31982730622,
                        "supply": 175879606086,
                        "watermark": 255810788786
                    },
                    "height": 6042,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PxVxfRr8",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6043,
                        "is_hidden": false,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "timestamp": 1615574830,
                        "username": "diamondhands"
                    },
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "timestamp": 1615574505
                },
                "sender": {
                    "balance": 33447301750,
                    "coin": {
                        "locked": 480232732699,
                        "price": 6132459458,
                        "supply": 78309972683,
                        "watermark": 79534264925
                    },
                    "height": 9768,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Rg4v2QyWq1z",
                        "description": "GiftClout.com\ud83d\udc9d :: The Gift Economy Social Network\n\nApply for Verification \u2705 during our open beta. \n\nIncludes:\n\n- Invitation to Private Beta Tester Telegram Group\n\n- Whitelisted in GiftClout\u2019s Global Feed\n\n- Inclusion in Our Supporters section \n\nYou can apply for verification by contributing to the $GiftClout coin when you hold 0.1 or more.",
                        "height": 9775,
                        "is_hidden": false,
                        "reward_points": 2200,
                        "stake_points": 12500,
                        "timestamp": 1616712097,
                        "username": "GiftClout"
                    },
                    "pubkey": "BC1YLhKYCXfy2tguomfrydUAEFcf5ANqkaQELWgTHWVVNPB3UHibxth",
                    "timestamp": 1616709041
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

**count** – how many rows total in your request.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.stat.list", "params": {"hash":"1b50b5bf8bf7190d60f938443f825de447b01ee865a96b08e1ae5461ad4b5c24", "period": "hour", "start_at": 1618895843, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 6180,
            "list": [
                {
                    "ts": 1618887600,
                    "like_count": 0,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0
                },
                {
                    "ts": 1618891200,
                    "like_count": 1,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.rank.list

Ranked post list

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>What type of rankings we need to get. Default is <code>diamond_value</code>. Allowed values: <code>diamond_value</code>, <code>like_count</code>,  <code>repost_count</code>,<code>comment_count</code></td></tr><tr><td>sorting</td><td></td><td>false</td><td>One of: value or change.<br><code>value</code> – we sort by value for all time.<br><code>change</code> – we sort by daily change on request value rank.</td></tr><tr><td>range</td><td></td><td>false</td><td>Represents list with min max values or default []. First index - min, second one - max. In case you pass it you will get narrowed ranking in this range</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

Returns list of posts ranked by requested type

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.rank.list", "params": {"type":"like_count", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 3874120,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "wwhat happen with u",
                    "lang": "jv",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1620337352,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1626698046,
                        "like_count": 3759,
                        "diamond_count": 6,
                        "diamond_value": 5406860,
                        "repost_count": 1919,
                        "quote_count": 2,
                        "comment_count": 2067,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "rank": {
                        "position": 1,
                        "change": 0
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "Nodes are faster\nThe password is gone\nDo your worst 😈\n\nWhat made things faster? Click for details 👇",
                    "lang": "en",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1617168348,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1640646369,
                        "like_count": 2183,
                        "diamond_count": 21,
                        "diamond_value": 11028188,
                        "repost_count": 4,
                        "quote_count": 2,
                        "comment_count": 907,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
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
