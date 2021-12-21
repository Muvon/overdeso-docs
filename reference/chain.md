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
            "btc_usd_rate": 4846100,
            "create_nft_fee": 10000,
            "create_profile_fee": 1000000,
            "max_nft_copies": 1000,
            "min_fee_per_kb": 1000,
            "usd_rate": 3198
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### chain.stat.get

Get global chain statistic

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>false</td><td>One of: account, post, hashtag.</td></tr></tbody></table>

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
            "balance": 0,
            "coin_buy_count": 0,
            "coin_buy_value": 0,
            "coin_gain": 0,
            "coin_sell_count": 0,
            "coin_sell_value": 0,
            "comment_count": 0,
            "follower_count": 0,
            "following_count": 0,
            "holder_count": 0,
            "holding_count": 0,
            "locked": 0,
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
            "post_count": 0,
            "price": 0,
            "quote_count": 0,
            "receiver_coin_count": 0,
            "receiver_coin_value": 0,
            "receiver_connection_count": 0,
            "receiver_connection_value": 0,
            "receiver_diamond_count": 0,
            "receiver_diamond_value": 0,
            "receiver_nft_bid_count": 0,
            "receiver_post_like_count": 0,
            "receiver_seed_count": 0,
            "receiver_seed_value": 0,
            "repost_count": 0,
            "reward_coins": 0,
            "reward_value": 0,
            "sender_coin_count": 0,
            "sender_coin_value": 0,
            "sender_connection_count": 0,
            "sender_connection_value": 0,
            "sender_diamond_count": 0,
            "sender_diamond_value": 0,
            "sender_nft_bid_count": 0,
            "sender_post_like_count": 0,
            "sender_seed_count": 0,
            "sender_seed_value": 0,
            "supply": 0,
            "tx_count": 0,
            "utxo_count": 0,
            "watermark": 0
        }
    ]
]
```
{% endtab %}
{% endtabs %}

