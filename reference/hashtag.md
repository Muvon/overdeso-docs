---
description: Hashtag related methods.
---

# Hashtag

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
curl -s --data '[{"method":"hashtag.get", "params": {"hashtag":"bitclout"}}]' http://api.overdeso.lo/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "hashtag": "bitclout",
            "count": 10003,
            "last_ts": 1639143932
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### hashtag.list

Get most used hashtags for all time sorted by its usage and using last timestamp appeared

#### Request params

{% hint style="danger" %}
**last\_ts** is not used now. We are working on it to make it useful for the next update.
{% endhint %}

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>last_ts</td><td></td><td>false</td><td>Fetch hashtags that was last used only since this timestamp</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

The method returns most popular hashtags sorted by total usage time.

**count** – for now just calculated size of current returned list.

**list** – most popular hastags list.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.list", "params": {}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 10,
            "list": [
                {
                    "count": 10371,
                    "hashtag": "bitclout",
                    "last_ts": 0
                },
                {
                    "count": 4020,
                    "hashtag": "1",
                    "last_ts": 0
                },
                {
                    "count": 3496,
                    "hashtag": "nft",
                    "last_ts": 0
                },
                {
                    "count": 3019,
                    "hashtag": "bitcoin",
                    "last_ts": 0
                },
                {
                    "count": 1905,
                    "hashtag": "2",
                    "last_ts": 0
                },
                {
                    "count": 1400,
                    "hashtag": "rideordie",
                    "last_ts": 0
                },
                {
                    "count": 1398,
                    "hashtag": "crypto",
                    "last_ts": 0
                },
                {
                    "count": 1295,
                    "hashtag": "3",
                    "last_ts": 0
                },
                {
                    "count": 1222,
                    "hashtag": "cloutclub",
                    "last_ts": 0
                },
                {
                    "count": 1130,
                    "hashtag": "cloutted",
                    "last_ts": 0
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

**count** – contains current resulting datataset in response not total count of data we have.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"hashtag.stat.list", "params": {"hashtag":"bitclout", "period": "hour", "start_at": 1616174306, "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 10,
            "list": [
                {
                    "count": 0,
                    "ts": 1616173200
                },
                {
                    "count": 0,
                    "ts": 1616176800
                },
                {
                    "count": 50,
                    "ts": 1616180400
                },
                {
                    "count": 65,
                    "ts": 1616184000
                },
                {
                    "count": 65,
                    "ts": 1616187600
                },
                {
                    "count": 76,
                    "ts": 1616191200
                },
                {
                    "count": 77,
                    "ts": 1616194800
                },
                {
                    "count": 89,
                    "ts": 1616198400
                },
                {
                    "count": 94,
                    "ts": 1616202000
                },
                {
                    "count": 103,
                    "ts": 1616205600
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
