---
description: Message related methods
---

# ✉ Message

### message.list

Get list of messages for recipient or for sender account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>username</td><td></td><td>true</td><td>Username if requested account has profile</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>type</td><td></td><td>false</td><td>One of: sender or recipient. Default is recipient</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of messages sorted in chronological order (last to old)

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s -H 'X-Account-Username: donhardman' --data '[{"method":"message.list", "params": {"username": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 2342,
            "list": [
                {
                    "account": {
                        "balance": 552477149529,
                        "coin": {
                            "locked": 6576578540390,
                            "price": 35105629779,
                            "supply": 187336862538,
                            "watermark": 196240708275
                        },
                        "height": 10651,
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/QLRLb6SYLkM",
                            "description": "#1 Celebrity Brand \u2b50\ufe0f \n\nCollabs: @KevinHart4real, @Snoopdogg, @bellathorne, @6ix9ine, @tyga, @noah_schnapp, @Ab + MANY MORE\n\nFounders \ud83d\udd11 \n@jordanlintz @lukelintz @jacksonlintz",
                            "height": 10652,
                            "is_hidden": false,
                            "reward_points": 1500,
                            "stake_points": 12500,
                            "timestamp": 1617009351,
                            "username": "HighKey"
                        },
                        "pubkey": "BC1YLikh1xrhqtWWUrHjbZnwY7b9hi6RxjLPxu1Jc1qpnJevftdeUZD",
                        "stat": {
                            "coin_buy_count": 1281,
                            "coin_buy_value": 23411265445186,
                            "coin_sell_count": 536,
                            "coin_sell_value": 13610433553710,
                            "comment_count": 486,
                            "follower_count": 7769,
                            "following_count": 54,
                            "holder_count": 867,
                            "holding_count": 1842,
                            "nft_buy_count": 0,
                            "nft_buy_value": 0,
                            "nft_coin": 1906577693,
                            "nft_count": 3,
                            "nft_gain": 5719733079,
                            "nft_mint_count": 1,
                            "nft_mint_value": 5719733079,
                            "nft_royalty": 1906577693,
                            "nft_sell_count": 0,
                            "nft_sell_value": 0,
                            "post_count": 523,
                            "quote_count": 36,
                            "receiver_coin_count": 4849,
                            "receiver_coin_value": 1583212980452,
                            "receiver_connection_count": 41988,
                            "receiver_connection_value": 45450973878183,
                            "receiver_diamond_count": 5211,
                            "receiver_diamond_value": 17142328575,
                            "receiver_seed_count": 1,
                            "receiver_seed_value": 50000000,
                            "repost_count": 53,
                            "reward_coins": 28483086821,
                            "reward_value": 1791137114683,
                            "sender_coin_count": 580,
                            "sender_coin_value": 2460265276956,
                            "sender_connection_count": 139,
                            "sender_connection_value": 9673939619671,
                            "sender_diamond_count": 638,
                            "sender_diamond_value": 3757404342,
                            "sender_seed_count": 13,
                            "sender_seed_value": 1128951000000,
                            "tx_count": 26279,
                            "utxo_count": 14
                        },
                        "timestamp": 1617008554
                    },
                    "submitted_at": 1628839144,
                    "text_hex": "046b43ab92e582d5092f4e38bda4dcf7757a69c1d04c421687c8aa49608c8fd3aa528158986427d9e7e9017f6d0fb57a7c58a9e81609661fdc64f05cf95744052d149c573df2dd041b5e617224d52b92312a668f3a662cf18923ff68ff511575e99aa57250a8490bc2a9173e9d5eacac3df18c9e58467d6e912f2836414d8a5ddac497856a290d2ccc235aa56502ebab51b8159a3935f0fc15bb0a32eaacdb6e51498445196d8293fe1837665f1a85d1bfc28542a4417223c89def7ad377e6"
                },
                {
                    "account": {
                        "balance": 26922964385,
                        "coin": {
                            "locked": 68025784767,
                            "price": 1666412525,
                            "supply": 40821695555,
                            "watermark": 44631603462
                        },
                        "height": 37683,
                        "profile": {
                            "avatar_url": "https://overdeso.com/media/avatar/TgdnCyHTh5p",
                            "description": "Find top gainers or worst losers.\n\nTrack successful investors or creators to follow.\n\nEarly beta / We have API DM us\n\nWith \u2764\ufe0f by @muvon\nhttps://cloutomy.com",
                            "height": 37683,
                            "is_hidden": false,
                            "reward_points": 2000,
                            "stake_points": 12500,
                            "timestamp": 1624823636,
                            "username": "Cloutomy"
                        },
                        "pubkey": "BC1YLi54m8fVEL8sU3jQUNLSMA1ZagEqyrg9MeriPj4wZnrbNDuGoiG",
                        "stat": {
                            "coin_buy_count": 2,
                            "coin_buy_value": 4576896340,
                            "coin_sell_count": 0,
                            "coin_sell_value": 0,
                            "comment_count": 16,
                            "follower_count": 182,
                            "following_count": 30,
                            "holder_count": 36,
                            "holding_count": 43,
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
                            "post_count": 20,
                            "quote_count": 4,
                            "receiver_coin_count": 98,
                            "receiver_coin_value": 128092773254,
                            "receiver_connection_count": 645,
                            "receiver_connection_value": 211141073262,
                            "receiver_diamond_count": 103,
                            "receiver_diamond_value": 36327158,
                            "receiver_seed_count": 1,
                            "receiver_seed_value": 14999500,
                            "repost_count": 1,
                            "reward_coins": 0,
                            "reward_value": 33271967351,
                            "sender_coin_count": 4,
                            "sender_coin_value": 7653104131,
                            "sender_connection_count": 11,
                            "sender_connection_value": 7540000000,
                            "sender_diamond_count": 1,
                            "sender_diamond_value": 52492,
                            "sender_seed_count": 2,
                            "sender_seed_value": 10000000,
                            "tx_count": 717,
                            "utxo_count": 42
                        },
                        "timestamp": 1624823636
                    },
                    "submitted_at": 1628823463,
                    "text_hex": "040102afdde74141c66720e6c7698c976142b4f9eb350114b85d1876948c9c243e994422e2027b70c631c91ad726c07d7120050d10f37caff44d47d8bb7293e83cc2a1529e9a78138a072b93aa12012e3b25232abf4f24ff7abbaf2d8a0f709aaecf8e4d32beaf65cdbe05fd8ea5869fe432281575e4424271cbcf56ee9d9b41f0589b2004ea4bea685d8c06a6ea5c2b25d39021355417dafd361d9fa3e06d5372160a26fce5d6a9fcac40f4de785a1abf8c58b2d6d27e083eb4d2d8e1e536ce36c91fa55d130843967f8f2b163488d15abb12e906fd9afc210fa2ff61472c9a62241941dceeafc6c87fefa1d6ac4cb046103debf4cf71481fc65c5972d51b8fad18926ebe95186cdcba825724013d769ec1be4862cbf66d4f592284014e5818d66b6e2e82401aa5d58fa6fb52efa9fe42286f538392cf4dc437d52fc0d5e8af74f4cfbf237dd716fad1584719d9bd31bfb396dbd6c9c598e0014b1860e12da6795f4d23994650880e3a430e2aaf0e70c660d56c9799c9413d5fb488948369f2e19074515c700ca74c3705a8e88b82b33e4ca637ad32bf6e8cfcb8da6027b2996c4e8fefda37a4075ab13a117eea0e3f5a867ce8d6b9539ab29bf7f4bf661f782acbf069372e67ee5dd6996a5cd5f98d13013b1257705e6033ef31e6cf5170161dfa42798e2f20c59037678863aea0ec503721fd2e609a57d1012114dae9f7cfe69db1854e086726f92042debd28f91de5f232b792dd08a3784034cde92d86b5a7a3ae5bd5c367cf276e88b714c5880eb748bde460f7fb30e77e2c94119419c20e1dbc10c6645024f8d5de94ee34d444ddb68a43058d67f757908a08584238436431afa91caabe1fe499d93b21dd667b75e12c9e25717f15cf41457e515122166f69ea40306d34290a2f078eb336dd3e4a4b5e0ba42eee6ad90b32c1a1b092acaa81d3f3318bd183f72679ddd3afdfb9204ddc527d023fe80cc274ad717c61975d6e7fec47553c38f2cb67dc7b4a0c291a7449dd43925d27"
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
