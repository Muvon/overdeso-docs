---
description: Block related methods of API.
---

# Block

### block.tip

Get best block info with its height and hash.

#### Request params

No params required for this method.

#### Response

This method returns information about best block in chain.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"block.tip"}]' http://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "hash": "000000000000146a14a12b0d86cff44b9154718eeed9b6bdde31e33371683181",
            "height": 83898
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### block.get

Get block by height or hash.

Method requires to pass height or hash in hex format of requested block.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>height</td><td></td><td>true</td><td>Height of block to fetch. </td></tr><tr><td>hash</td><td></td><td>true</td><td>Block hash in hex format.</td></tr><tr><td>expand</td><td></td><td>false</td><td>By default we return all block transaction ids. But if we pass expand – we decode transactions in json objects and also limit output by using offset/limit params</td></tr><tr><td>offset</td><td></td><td>false</td><td>Starting offset to fetch list. Default is 0.</td></tr><tr><td>limit</td><td></td><td>false</td><td>How many transactions to fetch for request. Default is 10.</td></tr></tbody></table>

#### Response

The method returns parsed block information.&#x20;

**hash** contains block hash in hex format.

**header** contains parsed block header information.

**tx\_count** contains transaction count in this block.

**txs** contains tx ids or full info about transaction parsed if **extend** parameter passed.

**info** contains various aggregated info about transactions for this block.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -H 'Accept: application/json' --data '[{"method":"block.get", "params": {"height":1}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "header": {
                "height": 1,
                "merkle_hash": "fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c",
                "nonce": 88348,
                "hash": "00000016c72096930787c7e7de4ad069198c2137feddeecbe6a9ec4d61cb6870",
                "prev_hash": "5567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62",
                "raw": "000000005567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c59d03c60010000001c590100",
                "timestamp": 1614598233,
                "version": 0
            },
            "info": {
                "burned": 0,
                "fee": 0,
                "input_count": 0,
                "input_value": 0,
                "output_count": 1,
                "output_value": 1000000000,
                "tx_types": {
                    "BLOCK_REWARD": 1
                }
            },
            "tx_count": 1,
            "txs": [
                "3JuETkEpP92uwnvTDYvhB5uSyAXqG8fDBaUA9UasAijChf3ZAkUPDT"
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

