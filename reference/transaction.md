---
description: Transaction related methods of API.
---

# 💸 Transaction

### transaction.get

Get transaction by its id in base58 check format.

Returned transaction data are in hex.

#### Request

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td></td><td>true</td><td>Base58Check transaction id starting with 3J…</td></tr></tbody></table>

#### Response

The method returns structure with 3 fields: **block,** **tx** and **info**.&#x20;

**block** fields contains block header information if transaction is in block or null otherwise.&#x20;

**tx** field contains parsed data of requested transation.

**info** field contains extra information for this transaction.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl --data '[{"method":"transaction.get", "params": {"id":"3JuETVBKjuSk6VzZy6MsiYn4h8JZnK1cWmrDzHwMQBj4QqEY9tL4YJ"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "block": {
                "version": 0,
                "prev_hash": "000000000048653497ebd41ed653454e6d6dcb1fbb624995db35902eeeb65a18",
                "merkle_hash": "9c4c22c5236e34b0c42ef4c5416a591c854ca3187de39d73a32ff79f0b35a9e8",
                "timestamp": 1616456888,
                "height": 8999,
                "nonce": 1401535402,
                "raw": "00000000000000000048653497ebd41ed653454e6d6dcb1fbb624995db35902eeeb65a189c4c22c5236e34b0c42ef4c5416a591c854ca3187de39d73a32ff79f0b35a9e8b82c596027230000aabb8953"
            },
            "tx": {
                "id": "3JuETVBKjuSk6VzZy6MsiYn4h8JZnK1cWmrDzHwMQBj4QqEY9tL4YJ",
                "transactor": "BC1YLiMRq7HomqRApkL3tjCbZhnjEp8qdGeezxf3HVdBA7kBJM8KtzK",
                "type_id": 11,
                "inputs": [
                    [
                        "3JuEUMHcdufXRS51gqAcFKaAxWDEaCVxJBphdY4YJ8t3ysUZ4FKNyy",
                        0
                    ]
                ],
                "outputs": [
                    [
                        "BC1YLiMRq7HomqRApkL3tjCbZhnjEp8qdGeezxf3HVdBA7kBJM8KtzK",
                        17880942
                    ]
                ],
                "signature": "3045022100aa96e0b6d3d390a065326c73a5085988b3250e459fb6f1af86f27c50ff76b3b602207b078fb977a7c0dbf589cc92e780b1ab3b4a81175fa2ebef6a1711a7da1581a4",
                "meta": {
                    "pubkey": "BC1YLgXCHcJ7k4Fkad1o6qhmt9AcCBVX7zsq6hi4T13tBmgbne2873b",
                    "operation_id": 1,
                    "spend": 0,
                    "coins": 9000000,
                    "add": 0,
                    "value_expected": 508205434,
                    "coins_expected": 0
                },
                "extra": [],
                "size": 228,
                "raw": "01d45696865d1e0f80252aed04a8de09e2eec8b9aa18a3f5b9287ed0522a41362d0001036136977d43e271c2cedc137d00e6be7f47c6f5916a2025a7841dace59fb53473eeaec3080b2f21026fff411f5563795aa4df7b112457a7c959b45313c45d8ca9fd64344781f682f80100c0a8a50400fab2aaf2010021036136977d43e271c2cedc137d00e6be7f47c6f5916a2025a7841dace59fb5347300473045022100aa96e0b6d3d390a065326c73a5085988b3250e459fb6f1af86f27c50ff76b3b602207b078fb977a7c0dbf589cc92e780b1ab3b4a81175fa2ebef6a1711a7da1581a4"
            },
            "info": {
                "type_id": 11,
                "fee": 235,
                "burned": 67768,
                "input_count": 1,
                "input_value": 695488423,
                "output_count": 2,
                "output_value": 695488188,
                "outputs": [
                    [
                        "BC1YLiMRq7HomqRApkL3tjCbZhnjEp8qdGeezxf3HVdBA7kBJM8KtzK",
                        677607246
                    ]
                ]
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### transaction.list

Get list of transactions related to account by username or public key, block or mempool sorted in chronological way (new to old).

If user or block related request params are not present we return mempool transactions.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select" data-multiple>Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>block</td><td></td><td>false</td><td>Block hash in hex format or block height</td></tr><tr><td>account</td><td></td><td>false</td><td>Account username or public key</td></tr><tr><td>type_id</td><td></td><td>false</td><td>Get only wanted transaction types. Default is null. We fetch any.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start default is 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch for the request. Default is 10.</td></tr></tbody></table>

#### Response

Reposponse contains 2 keys: **count** and **list**.&#x20;

**list** contains simple list of transaction base58 check ids sorted in ascending order by time.

**count** – total count of transactions that related to this account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"transaction.list", "params": {"account":"diamondhands", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 72265,
            "list": [
                "3JuETwLjVhACqp3cja17363gQWGTLzgcCkwRNgY3uEnA2ecGRwiLW7",
                "3JuEUL3sFXn73B88zVx4PLtHCHE6LhtkhjZ5fWGn4o4VPsPRNZXMpb"
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### transaction.submit

Submit signed transaction to blockchain. One of 2 fields required: `raw` or `list` of transaction hexes to be passed.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>raw</td><td></td><td>true</td><td>Signed transaction in hex format to broadcast</td></tr><tr><td>list</td><td></td><td>true</td><td>List of transactions hexes to submit in one bundle</td></tr></tbody></table>

#### Responsex\`

Return 2 keys: `submit` and `skip`.

**submit** – contains **list** of tx ids submitted and **count** of it.

**skip** – contains **list** of raw tx hex data that skipped due error and **count** of it.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"transaction.submit", "params": {"raw": "02d8dd25b5dd4a75364bc679bef23c63a9666e163e33760bcdfbd9f6cb0fa198e30000476a9cce537e598f5420015ad1aa42374c05ebcd48d4ed64a09c283df542fc000203bd83700e23421e115eb56c760e13cf464dcb4220e48ce61cb20084a398776bd6d08603025fccf1467f0d9bfe749bc1d3b3217d16d48d238af28b79d2bd707a2c27e79e1da4dc02020021025fccf1467f0d9bfe749bc1d3b3217d16d48d238af28b79d2bd707a2c27e79e1d020c4469616d6f6e644c6576656c01020f4469616d6f6e64506f73744861736820a2f0abd7a36206db028f8f8cf845c61aa6415a9698568285c8185e708853c8ea463044022026d31681e4ff4311ada2e14b7ddb5842d39ac2b2337f3f0f80261adacb7a1dd5022064f9abe35de33d957c6edb6d79b3d342a7fe9817526992bd2698d1c60c33ded5"}}]' http://api.overdeso.lo/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "skip": {
                "count": 0,
                "list": []
            },
            "submit": {
                "count": 1,
                "list": [
                    "3JuETJasnB4YHgmGsLna5suepgSzpAVRxiQvSbUyN9jcDcddRuLY6R"
                ]
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}
