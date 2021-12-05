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

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

### block.get

Get block by height or hash.

Method requires to pass height or hash in hex format of requested block.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>height</td><td></td><td>true</td><td>Height of block to fetch. </td></tr><tr><td>hash</td><td></td><td>true</td><td>Block hash in hex format.</td></tr><tr><td>expand</td><td></td><td>false</td><td>By default we return all block transaction ids. But if we pass expand – we decode transactions in json objects and also limit output by using offset/limit params</td></tr><tr><td>offset</td><td></td><td>false</td><td>If expand passed we start to fetch transactions on this offset sorted by sequence in block</td></tr><tr><td>limit</td><td></td><td>false</td><td>If expand passed we fetch this amount of transactions.</td></tr></tbody></table>

#### Response

The method returns parsed block information.&#x20;

**hash** contains block hash in hex format.

**header** contains parsed block header information.

**tx\_counts** contains transaction count in this block.

**txs** contains tx ids or full info about transaction parsed if **extend** parameter passed.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -H 'Accept: application/json' --data '[{"method":"block.get", "params": {"height":1}}]' https://api.overdeso.com/v1 | python -m json.tool
```

{% code title="" %}
```json
[
    [
        null,
        {
            "hash": "00000016c72096930787c7e7de4ad069198c2137feddeecbe6a9ec4d61cb6870",
            "header": {
                "height": 1,
                "merkle_hash": "fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c",
                "nonce": 88348,
                "prev_hash": "5567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62",
                "raw": "000000005567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c59d03c60010000001c590100",
                "timestamp": 1614598233,
                "version": 0
            },
            "tx_count": 0,
            "txs": [
                "3JuETkEpP92uwnvTDYvhB5uSyAXqG8fDBaUA9UasAijChf3ZAkUPDT"
            ]
        }
    ]
]
```
{% endcode %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## Transaction

### transaction.get

Get transaction by its id in base58 check format.

Returned transaction data are in hex.

#### Request

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td></td><td>true</td><td>Height of block to fetch. </td></tr></tbody></table>

#### Response

The method returns structure with 2 fields: **block** and **tx**.&#x20;

**block** fields contains block header information if transaction is in block or null otherwise.&#x20;

**tx** field contains parsed data of requested transation.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl --data '[{"method":"transaction.get", "params": {"id":"3JuETkEpP92uwnvTDYvhB5uSyAXqG8fDBaUA9UasAijChf3ZAkUPDT"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "block": {
                "height": 1,
                "merkle_hash": "fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c",
                "nonce": 88348,
                "prev_hash": "5567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62",
                "raw": "000000005567c45b7b83b604f9ff5cb5e88dfc9ad7d5a1dd5818dd19e6d02466f47cbd62fd8e08af2ae7f62cdc9676ca3d9d6df9fa801c2263c494503ded47b4164bb88c59d03c60010000001c590100",
                "timestamp": 1614598233,
                "version": 0
            },
            "tx": {
                "extra": [],
                "id": "3JuETkEpP92uwnvTDYvhB5uSyAXqG8fDBaUA9UasAijChf3ZAkUPDT",
                "inputs": [],
                "meta": {
                    "extra_data": "97f68498b39985d0b101"
                },
                "outputs": [
                    [
                        "BC1YLgKZyfgyNntCMXAZYExM8JooYqrYvVsrR8d8XVxorDruYFdq31p",
                        1000000000
                    ]
                ],
                "raw": "000102559949a3a9bce770aa526b1006935f3f896645a4622add60f83a256adb557e368094ebdc03010b0a97f68498b39985d0b101000000",
                "signature": "",
                "size": 56,
                "transactor": "8mkU8yaVLs",
                "type_id": 1
            }
        }
    ]
]
```
{% endtab %}

{% tab title="Second Tab" %}

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

