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
curl -s --data '[{"method":"block.list", "params": {"limit": 5}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 86225,
            "list": [
                {
                    "hash": "0000000000006628dcbc44d6ddf7b5c8ac4c4abe0fa525586bbb342958e65005",
                    "header": {
                        "extra_nonce": 7179487839102741002,
                        "height": 86224,
                        "merkle_hash": "cfefde56ea360f0b4afba70ee20de0ad098b2ffffdd6ee88ceaa51dd849d0a8d",
                        "nonce": 3418252571677542163,
                        "prev_hash": "00000000000006023d8ec7938786c563145de1cacfd7b4a711d49a59a1729734",
                        "raw": "0000000100000000000006023d8ec7938786c563145de1cacfd7b4a711d49a59a1729734cfefde56ea360f0b4afba70ee20de0ad098b2ffffdd6ee88ceaa51dd849d0a8d0000000061b71e1000000000000150d02f70129a6f67c71363a2aa26aef4aa0a",
                        "timestamp": 1639390736,
                        "version": 1
                    },
                    "info": {
                        "burned": 3119679,
                        "fee": 3347752,
                        "input_count": 1131,
                        "input_value": 14151550444932,
                        "output_count": 1153,
                        "output_value": 14151647444932,
                        "tx_types": {
                            "ACCEPT_NFT_BID": 1,
                            "BASIC_TRANSFER": 37,
                            "BLOCK_REWARD": 1,
                            "CREATOR_COIN": 3,
                            "FOLLOW": 237,
                            "LIKE": 741,
                            "NFT_TRANSFER": 1,
                            "PRIVATE_MESSAGE": 5,
                            "SUBMIT_POST": 78,
                            "UPDATE_NFT": 3,
                            "UPDATE_PROFILE": 6
                        }
                    },
                    "tx_count": 1113
                },
                {
                    "hash": "00000000000006023d8ec7938786c563145de1cacfd7b4a711d49a59a1729734",
                    "header": {
                        "extra_nonce": 8500080731704281445,
                        "height": 86223,
                        "merkle_hash": "fa1555eb6b7ec3718fae35af4ae2fb51760b11155091eb90ff8c51da788c7f89",
                        "nonce": 67554101734454144,
                        "prev_hash": "0000000000003e1875f6a9389d1f1db7b6a72ea4da35d2cf5fd1f18de1b8d1e5",
                        "raw": "000000010000000000003e1875f6a9389d1f1db7b6a72ea4da35d2cf5fd1f18de1b8d1e5fa1555eb6b7ec3718fae35af4ae2fb51760b11155091eb90ff8c51da788c7f890000000061b71bd000000000000150cf00f00018fd00b38075f65a63df604965",
                        "timestamp": 1639390160,
                        "version": 1
                    },
                    "info": {
                        "burned": 7049,
                        "fee": 84450,
                        "input_count": 309,
                        "input_value": 5270217495,
                        "output_count": 314,
                        "output_value": 5370217495,
                        "tx_types": {
                            "ACCEPT_NFT_TRANSFER": 2,
                            "BASIC_TRANSFER": 4,
                            "BLOCK_REWARD": 1,
                            "BURN_NFT": 1,
                            "CREATOR_COIN": 5,
                            "FOLLOW": 48,
                            "LIKE": 203,
                            "NFT_BID": 1,
                            "PRIVATE_MESSAGE": 1,
                            "SUBMIT_POST": 35,
                            "UPDATE_NFT": 3,
                            "UPDATE_PROFILE": 2
                        }
                    },
                    "tx_count": 306
                },
                {
                    "hash": "0000000000003e1875f6a9389d1f1db7b6a72ea4da35d2cf5fd1f18de1b8d1e5",
                    "header": {
                        "extra_nonce": -4110651364934265547,
                        "height": 86222,
                        "merkle_hash": "1a03cf9348119715f4a13caf98648aad7598d030b98edccebf86184d8f6da69f",
                        "nonce": "18206162853297210034",
                        "prev_hash": "00000000000031798b899231a5f3029aa1c78bba2f4b33706e1d66e3df38d16b",
                        "raw": "0000000100000000000031798b899231a5f3029aa1c78bba2f4b33706e1d66e3df38d16b1a03cf9348119715f4a13caf98648aad7598d030b98edccebf86184d8f6da69f0000000061b71b3700000000000150cefca948a799b142b2c6f4085cdd9e5535",
                        "timestamp": 1639390007,
                        "version": 1
                    },
                    "info": {
                        "burned": 2471040,
                        "fee": 2240313,
                        "input_count": 825,
                        "input_value": 7487053967358,
                        "output_count": 828,
                        "output_value": 7487151957358,
                        "tx_types": {
                            "ACCEPT_NFT_TRANSFER": 2,
                            "AUTHORIZE_DERIVED_KEY": 1,
                            "BASIC_TRANSFER": 47,
                            "BLOCK_REWARD": 1,
                            "CREATE_NFT": 1,
                            "CREATOR_COIN": 4,
                            "FOLLOW": 67,
                            "LIKE": 599,
                            "NFT_BID": 1,
                            "SUBMIT_POST": 46,
                            "UPDATE_NFT": 3,
                            "UPDATE_PROFILE": 2
                        }
                    },
                    "tx_count": 774
                },
                {
                    "hash": "00000000000031798b899231a5f3029aa1c78bba2f4b33706e1d66e3df38d16b",
                    "header": {
                        "extra_nonce": -213718797776711624,
                        "height": 86221,
                        "merkle_hash": "7e09c27db9d084ed30537c1df14d19d875116c8309b87254a03bd0c2b15ef2d5",
                        "nonce": 22518125381160777,
                        "prev_hash": "00000000000042f216f8eae5b0715fec49032a7ce517b8dc3420c63d133da8f7",
                        "raw": "0000000100000000000042f216f8eae5b0715fec49032a7ce517b8dc3420c63d133da8f77e09c27db9d084ed30537c1df14d19d875116c8309b87254a03bd0c2b15ef2d50000000061b719b300000000000150cd0050001da05a0f49fd08b7e2c0b21038",
                        "timestamp": 1639389619,
                        "version": 1
                    },
                    "info": {
                        "burned": 1024974,
                        "fee": 1146509,
                        "input_count": 567,
                        "input_value": 2042506872970,
                        "output_count": 583,
                        "output_value": 2042605862970,
                        "tx_types": {
                            "BASIC_TRANSFER": 27,
                            "BLOCK_REWARD": 1,
                            "CREATE_NFT": 1,
                            "CREATOR_COIN": 4,
                            "FOLLOW": 58,
                            "LIKE": 410,
                            "PRIVATE_MESSAGE": 4,
                            "SUBMIT_POST": 40,
                            "UPDATE_NFT": 1,
                            "UPDATE_PROFILE": 3
                        }
                    },
                    "tx_count": 549
                },
                {
                    "hash": "00000000000042f216f8eae5b0715fec49032a7ce517b8dc3420c63d133da8f7",
                    "header": {
                        "extra_nonce": -3852662863127401814,
                        "height": 86220,
                        "merkle_hash": "f57c2aedb1cbcc38e390ae3158bd7e8e1943fb6e58078c13b88d55c34c5c5310",
                        "nonce": "12185549923806625866",
                        "prev_hash": "0000000000001f1525735a27e376d5c91ff2cce8e2b55babe454abe142140858",
                        "raw": "000000010000000000001f1525735a27e376d5c91ff2cce8e2b55babe454abe142140858f57c2aedb1cbcc38e390ae3158bd7e8e1943fb6e58078c13b88d55c34c5c53100000000061b7188d00000000000150cca91bc5180948404aca889789cbf3aaaa",
                        "timestamp": 1639389325,
                        "version": 1
                    },
                    "info": {
                        "burned": 0,
                        "fee": 14949,
                        "input_count": 64,
                        "input_value": 19425522085,
                        "output_count": 69,
                        "output_value": 19525522085,
                        "tx_types": {
                            "BASIC_TRANSFER": 6,
                            "BLOCK_REWARD": 1,
                            "FOLLOW": 7,
                            "LIKE": 43,
                            "PRIVATE_MESSAGE": 1,
                            "SUBMIT_POST": 5
                        }
                    },
                    "tx_count": 63
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
