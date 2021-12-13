---
description: Blockchain related methods
---

# Chain

### chain.state

Method returns current chain state that is set by `UPDATE_GLOBAL_PARAMS` transaction

#### Request params

This method does not require any params to be passed.

#### Response

The method returns information of [chain state structure](structures.md#chain-state).

{% hint style="danger" %}
`usd_rate` is locked for blockchain genesis block time and not reflecting now. We are working on it.
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
