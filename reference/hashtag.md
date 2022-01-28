---
description: Hashtag related methods.
---

# #⃣ Hashtag

### hashtag.get

Get hashtag information .

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hashtag</td><td></td><td>true</td><td>Hashtag as text representation that follows regexp: <strong>/(?:#)(\p{L}\p{N}_?)/</strong></td></tr></tbody></table>

#### Response

Returns short information about wanted hashtag.

**count** – total times hashtag used.

**last\_ts** – timestamp of last usage of this hashtag.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.get", "params": {"hashtag":"deso"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "hashtag": "deso",
            "count": 4776,
            "last_ts": 1641136105
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### hashtag.list

Get recent used hashtags filtered by min time when it was last time used since

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>last_ts</td><td></td><td>false</td><td>Fetch hashtags that was last used only since this timestamp</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

The method returns most recent hashtags sorted by recent usage time.

**count** – for now just calculated size of current returned list.

**list** – most popular hastags list.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.list"}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 140563,
            "list": [
                {
                    "hashtag": "0",
                    "count": 74961,
                    "last_ts": 1641134229
                },
                {
                    "hashtag": "1",
                    "count": 15735,
                    "last_ts": 1641134543
                },
                {
                    "hashtag": "bitclout",
                    "count": 15046,
                    "last_ts": 1641114754
                },
                {
                    "hashtag": "nft",
                    "count": 11269,
                    "last_ts": 1641136105
                },
                {
                    "hashtag": "2",
                    "count": 5577,
                    "last_ts": 1641134543
                },
                {
                    "hashtag": "bitcoin",
                    "count": 4982,
                    "last_ts": 1641134229
                },
                {
                    "hashtag": "deso",
                    "count": 4776,
                    "last_ts": 1641136105
                },
                {
                    "hashtag": "3",
                    "count": 3843,
                    "last_ts": 1641121390
                },
                {
                    "hashtag": "crypto",
                    "count": 3545,
                    "last_ts": 1641124417
                },
                {
                    "hashtag": "cloutnft",
                    "count": 3396,
                    "last_ts": 1641079411
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### hashtag.stat.list

Get hasthags historical usage statistic.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hashtag</td><td></td><td>true</td><td>Hashtag to get statistic for</td></tr><tr><td>period</td><td></td><td>false</td><td>Aggregation period. One of: hour, day, month. Default is hour</td></tr><tr><td>start_at</td><td></td><td>false</td><td>Timestamp to start our lookup. Default is 1610948544 that is genesis block timestamp. That means we fetch from first stat record.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns statistic related data in chronological order (low to high).

**count** – total hashtags returned by your request.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.stat.list", "params": {"hashtag":"bitclout", "period": "hour", "start_at": 1616174306, "limit": 3}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 6936,
            "list": [
                {
                    "ts": 1616173200,
                    "count": 0
                },
                {
                    "ts": 1616176800,
                    "count": 0
                },
                {
                    "ts": 1616180400,
                    "count": 49
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### hashtag.post.list

Fetch posts for some hashtag in chronological order

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hashtag</td><td></td><td>false</td><td>Wanted hashtag as text</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

Returns list of post structures for requested hashtag.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.post.list", "params": {"hashtag":"deso", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 4778,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "Dazlin #DeSo Diamonds 💎 Power of 10 x 4 forced matrix Pay It Forward Strategy 🤑💵🤑🇹🇭💖🇨🇦😎✌️💎🙏💎",
                    "lang": "en",
                    "has_media": true,
                    "has_image": false,
                    "has_video": true,
                    "media": {
                        "embed_video_url": "https://www.youtube.com/embed/0fKBhvDjuy0"
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1641224941,
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
                    "hash": "3e2f3c00329bb1e049935a38203a51bf22a576b581d5c396a7c96a506ac9997d",
                    "account": {
                        "height": 63871,
                        "pubkey": "BC1YLjCZCNGu1h8tmvGqk8rnVFJamMZFyWncWtPvqMT2H2YCt5kk6xp",
                        "balance": 193289271,
                        "timestamp": 1632666513,
                        "profile": {
                            "timestamp": 1632714520,
                            "is_hidden": false,
                            "height": 64003,
                            "username": "Billythai1",
                            "description": "Paying It Forward 💎\n✅ @verifiedprofile ➡ \nbit.ly/3vFvNKY\nDazlin $DeSo Diamonds \nhttps://instantrecall.app.link/?referral_Code=WILLE11\nIG: @BillyArtLove\nTwitter: @BillyWarhol2\n",
                            "avatar_url": "https://overdeso.com/media/avatar/Sr8R4T3WsGD",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 6081913639,
                            "locked": 224968112,
                            "watermark": 9536126426,
                            "price": 36989691
                        }
                    },
                    "repost": null,
                    "root": null,
                    "parent": null,
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

### hashtag.rank.list

Get ranked list of hashtags

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>sorting</td><td></td><td>false</td><td>One of: value or change.<br><code>value</code> – we sort by count for all time.<br><code>change</code> – we sort by daily change on request count rank.</td></tr><tr><td>range</td><td></td><td>false</td><td>Represents list with min max values or default []. First index - min, second one - max. In case you pass it you will get narrowed ranking in this range</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

Returns list of hashtags ranked count of usage

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.rank.list", "params": {"offset": 0, "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 140563,
            "list": [
                {
                    "hashtag": "0",
                    "count": 74961,
                    "last_ts": 1641134229,
                    "rank": {
                        "position": 1,
                        "change": 0
                    }
                },
                {
                    "hashtag": "1",
                    "count": 15735,
                    "last_ts": 1641134543,
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
