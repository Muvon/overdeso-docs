---
description: Transaction related methods of API.
---

# Transaction

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
                "height": 8999,
                "merkle_hash": "9c4c22c5236e34b0c42ef4c5416a591c854ca3187de39d73a32ff79f0b35a9e8",
                "nonce": 1401535402,
                "prev_hash": "000000000048653497ebd41ed653454e6d6dcb1fbb624995db35902eeeb65a18",
                "raw": "00000000000000000048653497ebd41ed653454e6d6dcb1fbb624995db35902eeeb65a189c4c22c5236e34b0c42ef4c5416a591c854ca3187de39d73a32ff79f0b35a9e8b82c596027230000aabb8953",
                "timestamp": 1616456888,
                "version": 0
            },
            "info": {
                "burned": 67768,
                "fee": 235,
                "input_count": 1,
                "input_value": 695488423,
                "output_count": 2,
                "output_value": 695488188,
                "outputs": [
                    [
                        "BC1YLiMRq7HomqRApkL3tjCbZhnjEp8qdGeezxf3HVdBA7kBJM8KtzK",
                        677607246
                    ]
                ],
                "size": 228,
                "type_id": 11
            },
            "tx": {
                "extra": [],
                "id": "3JuETVBKjuSk6VzZy6MsiYn4h8JZnK1cWmrDzHwMQBj4QqEY9tL4YJ",
                "inputs": [
                    [
                        "3JuEUMHcdufXRS51gqAcFKaAxWDEaCVxJBphdY4YJ8t3ysUZ4FKNyy",
                        0
                    ]
                ],
                "meta": {
                    "add": 0,
                    "coins": 9000000,
                    "coins_expected": 0,
                    "operation_id": 1,
                    "pubkey": "BC1YLgXCHcJ7k4Fkad1o6qhmt9AcCBVX7zsq6hi4T13tBmgbne2873b",
                    "spend": 0,
                    "value_expected": 508205434
                },
                "outputs": [
                    [
                        "BC1YLiMRq7HomqRApkL3tjCbZhnjEp8qdGeezxf3HVdBA7kBJM8KtzK",
                        17880942
                    ]
                ],
                "raw": "01d45696865d1e0f80252aed04a8de09e2eec8b9aa18a3f5b9287ed0522a41362d0001036136977d43e271c2cedc137d00e6be7f47c6f5916a2025a7841dace59fb53473eeaec3080b2f21026fff411f5563795aa4df7b112457a7c959b45313c45d8ca9fd64344781f682f80100c0a8a50400fab2aaf2010021036136977d43e271c2cedc137d00e6be7f47c6f5916a2025a7841dace59fb5347300473045022100aa96e0b6d3d390a065326c73a5085988b3250e459fb6f1af86f27c50ff76b3b602207b078fb977a7c0dbf589cc92e780b1ab3b4a81175fa2ebef6a1711a7da1581a4",
                "signature": "3045022100aa96e0b6d3d390a065326c73a5085988b3250e459fb6f1af86f27c50ff76b3b602207b078fb977a7c0dbf589cc92e780b1ab3b4a81175fa2ebef6a1711a7da1581a4",
                "size": 228,
                "transactor": "BC1YLiMRq7HomqRApkL3tjCbZhnjEp8qdGeezxf3HVdBA7kBJM8KtzK",
                "type_id": 11
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### transaction.list

Get list of transactions related to account by username or public key.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start default is 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>Limit to fetch for the request. Default is 10.</td></tr></tbody></table>

#### Response

Reposponse contains 2 keys: **count** and **list**.&#x20;

**list** contains simple list of transaction base58 check ids sorted in ascending order by time.

**count** – total count of transactions that related to this account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"transaction.list", "params": {"username":"diamondhands", "limit": 10}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 100,
            "list": [
                "3JuEUJYnWFz7qG2Rh6JEakuwYQeEPnoCq12R1cH89kszGDpkHuU1QV",
                "3JuEU9nW6mj1JLyMnTihH3qCWvfcxh614ieC1k7asheuiK5rMSeiGt",
                "3JuETD2oxFoNVoHHzRVV5gSYeTB11GCB5ko4g3NtMKaBvwvTyHXUoE",
                "3JuETdiQvQ8RsvsVuczvPk4HHiZymtPBVjrRTLVzuM2WPnyHWFu8jD",
                "3JuETtCCiUM1VMcA6FyRkiJe2o9gt1DG9UfR66WhbiUqwCuDDZZNZb",
                "3JuETPx7hjnFHJsaz5UpK5CxgwBHN64S2GY22QDejWvoa25pLkQsax",
                "3JuETV6q86iJhLkAPSmCveP6jzVD5dSjyrHVrntMCuzWLAyGYRZyJK",
                "3JuESmsrbdbsUaajRA7J2nAH7E4nu5R1ijHJ1WHPPENYEX1JtHbinv",
                "3JuEUNVXanBrFLjrvbAW26TwxbHAvkH9dSzDoVHpADA9H2stF6Q9DZ",
                "3JuESujUvQKN6PgoWwT5quqFc9xjbpJ3F8wd2pev8EiVwgUnXf81T4"
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### transaction.submit

Submit signed transaction to blockchain. TODO: implementation in progresss
