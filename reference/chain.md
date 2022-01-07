---
description: Blockchain related methods
---

# ⛓ Chain

### chain.state

Method returns current chain state that is set by `UPDATE_GLOBAL_PARAMS` transaction

#### Request params

This method does not require any params to be passed.

#### Response

The method returns information of [chain state structure](structures.md#chain-state).

{% hint style="danger" %}
`usd_rate` is locked for blockchain genesis block time and not reflecting now. We are working on it. Estimate – next update ;)
{% endhint %}

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"chain.state"}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "min_fee_per_kb": 1000,
            "create_profile_fee": 1000000,
            "usd_rate": 3198,
            "create_nft_fee": 10000,
            "max_nft_copies": 1000,
            "btc_usd_rate": 4846100
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### chain.stat.get

Get blockchain accumulated statistic informationin whole network.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>false</td><td>One of: account, post, hashtag, transaction.</td></tr></tbody></table>

#### Response

Return global accumulated statistic for requested type.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"chain.stat.get", "params": {"type": "account"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "following_count": 12421984,
            "holding_count": 1440004,
            "locked": 693308634568853,
            "balance": 9877740202137228,
            "utxo_count": 1075952,
            "coin_buy_count": 2643594,
            "coin_buy_value": 5462082013499304,
            "coin_sell_count": 1882997,
            "coin_sell_value": 4227853799997282,
            "coin_gain": -266346112069366,
            "sender_coin_count": 3021906,
            "sender_coin_value": 304352236778259,
            "reward_value": 668373714535131,
            "sender_diamond_count": 3911440,
            "sender_diamond_value": 12211184013124,
            "sender_post_like_count": 18427841,
            "post_count": 2305625,
            "repost_count": 1039695,
            "quote_count": 399595,
            "comment_count": 3628409,
            "nft_count": 0,
            "nft_royalty": 2005619952120,
            "nft_coin": 2763915367710,
            "nft_mint_count": 46926,
            "nft_mint_value": 17602470932088,
            "nft_buy_count": 47880,
            "nft_buy_value": 24639096438291,
            "nft_sell_count": 954,
            "nft_sell_value": 2238766017758,
            "nft_gain": 17941948291453,
            "sender_nft_bid_count": 4252
        }
    ]
]
```
{% endtab %}
{% endtabs %}

