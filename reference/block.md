---
description: Block related methods of API.
---

# 🟦 Block

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
curl -s --data '[{"method":"block.tip"}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "height": 92009,
            "hash": "0000000000001c90ffc88497f725043182ea7536e9d0963b76f278e425d4950d"
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

<table><thead><tr><th>Param</th><th data-type="select" data-multiple>Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>block</td><td></td><td>true</td><td>Block height as integer or block hash in hex format as string</td></tr><tr><td>expand</td><td></td><td>false</td><td>By default we return all block transaction ids. But if we pass expand – we decode transactions in json objects and also limit output by using offset/limit params</td></tr><tr><td>offset</td><td></td><td>false</td><td>Starting offset to fetch list. Default is 0.</td></tr><tr><td>limit</td><td></td><td>false</td><td>How many transactions to fetch for request. Default is 10.</td></tr></tbody></table>

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
curl -H 'Accept: application/json' --data '[{"method":"block.get", "params": {"block":1}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "header": {
                "version": 0,
                "prev_hash": "5567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62",
                "merkle_hash": "fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c",
                "timestamp": 1614598233,
                "height": 1,
                "nonce": 88348,
                "raw": "000000005567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c59d03c60010000001c590100"
            },
            "hash": "00000016c72096930787c7e7de4ad069198c2137feddeecbe6a9ec4d61cb6870",
            "info": {
                "fee": 0,
                "burned": 0,
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

### block.list

Get latest mined blocks as a list

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>offset</td><td></td><td>false</td><td>Starting offset to fetch list. Default is 0.</td></tr><tr><td>limit</td><td></td><td>false</td><td>How many transactions to fetch for request. Default is 10.</td></tr></tbody></table>

#### Response

The method returns short information about blocks without transaction included as a list.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"block.list", "params": {"limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 92010,
            "list": [
                {
                    "header": {
                        "version": 1,
                        "prev_hash": "0000000000003c5017f4f3572775238dc75de849f94957206ca951836de50484",
                        "merkle_hash": "2f264f931b5073453b3c5cb152a65d8d8064972541a4bfac88c49cdc897b9858",
                        "timestamp": 1641136883,
                        "height": 92009,
                        "nonce": 4503839008854118,
                        "extra_nonce": -7803006394237052228,
                        "raw": "000000010000000000003c5017f4f3572775238dc75de849f94957206ca951836de504842f264f931b5073453b3c5cb152a65d8d8064972541a4bfac88c49cdc897b98580000000061d1c2f3000000000001676900100037bc3f906693b62706cb661abc"
                    },
                    "hash": "0000000000001c90ffc88497f725043182ea7536e9d0963b76f278e425d4950d",
                    "info": {
                        "fee": 2024726,
                        "burned": 2069904,
                        "input_count": 78,
                        "input_value": 460149783582,
                        "output_count": 64,
                        "output_value": 460247783582,
                        "tx_types": {
                            "BLOCK_REWARD": 1,
                            "BASIC_TRANSFER": 3,
                            "PRIVATE_MESSAGE": 1,
                            "SUBMIT_POST": 11,
                            "UPDATE_PROFILE": 3,
                            "FOLLOW": 5,
                            "LIKE": 28,
                            "CREATOR_COIN": 2,
                            "CREATOR_COIN_TRANSFER": 4,
                            "AUTHORIZE_DERIVED_KEY": 1
                        }
                    },
                    "tx_count": 59
                },
                {
                    "header": {
                        "version": 1,
                        "prev_hash": "000000000000426a0f4748d5409e6ee491b87e752e33ad1d33b9adee93467872",
                        "merkle_hash": "aa0ffdacdb27f9ccc207b004ed7294fbe040dbe1d85135a087f17f00e18abe7d",
                        "timestamp": 1641136831,
                        "height": 92008,
                        "nonce": 22518541669540663,
                        "extra_nonce": -3637538693919526830,
                        "raw": "00000001000000000000426a0f4748d5409e6ee491b87e752e33ad1d33b9adee93467872aa0ffdacdb27f9ccc207b004ed7294fbe040dbe1d85135a087f17f00e18abe7d0000000061d1c2bf00000000000167680050007e8d12a337cd84ddd494303052"
                    },
                    "hash": "0000000000003c5017f4f3572775238dc75de849f94957206ca951836de50484",
                    "info": {
                        "fee": 5691063,
                        "burned": 6316194,
                        "input_count": 956,
                        "input_value": 4406888614532,
                        "output_count": 970,
                        "output_value": 4406983514532,
                        "tx_types": {
                            "BLOCK_REWARD": 1,
                            "BASIC_TRANSFER": 126,
                            "PRIVATE_MESSAGE": 5,
                            "SUBMIT_POST": 118,
                            "UPDATE_PROFILE": 10,
                            "FOLLOW": 101,
                            "LIKE": 317,
                            "CREATOR_COIN": 39,
                            "CREATOR_COIN_TRANSFER": 45,
                            "CREATE_NFT": 10,
                            "UPDATE_NFT": 1,
                            "NFT_BID": 1,
                            "ACCEPT_NFT_TRANSFER": 4
                        }
                    },
                    "tx_count": 778
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
