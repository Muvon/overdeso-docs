---
description: Diamond related api methods
---

# Diamond

### diamond.list

Fetch diamond list for post hash or account as receiver or sender.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>pubkey</td><td></td><td>true</td><td>Public key in base 58 check format starting with BC1…</td></tr><tr><td>username</td><td></td><td>true</td><td>Username to fetch account for</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns structure as list each on with keys:

* **diamond** – contains level only of diamond;
* **post** – related post information;
* **sender** – information about sender account;
* **receiver** – information about receiver account.

If no diamonds found returned empty array list there was no error.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"diamond.list", "params": {"username": "diamondhands"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "diamond": {
                    "level": 6,
                    "value": 5000000000
                },
                "post": {
                    "account": {
                        "height": 6055,
                        "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8"
                    },
                    "coin": {
                        "locked": 2459499208919,
                        "price": 18220683927,
                        "supply": 134983912720,
                        "watermark": 166627229450
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsYUFsRZEjH",
                        "description": "The Community Builder \ud83d\udc4f\n\n@GiftClout\ud83d\udc9d\n@VerifiedProfile\u2705\n\ud83d\ude4f JUST HODL @frbuyback & @socialtrustfund \ud83d\ude4f \n\nDay 21 of 60 \ud83d\ude80 to the \ud83c\udf1d",
                        "height": 6062,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "RajLahoti"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 6055,
                        "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8"
                    },
                    "coin": {
                        "locked": 2459499208919,
                        "price": 18220683927,
                        "supply": 134983912720,
                        "watermark": 166627229450
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsYUFsRZEjH",
                        "description": "The Community Builder \ud83d\udc4f\n\n@GiftClout\ud83d\udc9d\n@VerifiedProfile\u2705\n\ud83d\ude4f JUST HODL @frbuyback & @socialtrustfund \ud83d\ude4f \n\nDay 21 of 60 \ud83d\ude80 to the \ud83c\udf1d",
                        "height": 6062,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "RajLahoti"
                    }
                }
            },
            {
                "diamond": {
                    "level": 6,
                    "value": 5000000000
                },
                "post": {
                    "account": {
                        "height": 9768,
                        "pubkey": "BC1YLhKYCXfy2tguomfrydUAEFcf5ANqkaQELWgTHWVVNPB3UHibxth"
                    },
                    "coin": {
                        "locked": 77812301643,
                        "price": 1822632011,
                        "supply": 42692272026,
                        "watermark": 66920220515
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Rg4vBr8mzKZ",
                        "description": "\u2705 Official @GiftClout\ud83d\udc9d | We send new creators \uff0411.11 of \ud83d\udcb2clout to get them started on their journey \ud83d\ude4f\ud83c\udffd\n\n33.33% FR \n> 1/2 supporting new users\n> 1/2 re-invested into our coin",
                        "height": 9776,
                        "is_hidden": 0,
                        "reward_points": 3333,
                        "stake_points": 12500,
                        "username": "GiftClout"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 9768,
                        "pubkey": "BC1YLhKYCXfy2tguomfrydUAEFcf5ANqkaQELWgTHWVVNPB3UHibxth"
                    },
                    "coin": {
                        "locked": 77812301643,
                        "price": 1822632011,
                        "supply": 42692272026,
                        "watermark": 66920220515
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Rg4vBr8mzKZ",
                        "description": "\u2705 Official @GiftClout\ud83d\udc9d | We send new creators \uff0411.11 of \ud83d\udcb2clout to get them started on their journey \ud83d\ude4f\ud83c\udffd\n\n33.33% FR \n> 1/2 supporting new users\n> 1/2 re-invested into our coin",
                        "height": 9776,
                        "is_hidden": 0,
                        "reward_points": 3333,
                        "stake_points": 12500,
                        "username": "GiftClout"
                    }
                }
            },
            {
                "diamond": {
                    "level": 1,
                    "value": 50000
                },
                "post": {
                    "account": {
                        "height": 6557,
                        "pubkey": "BC1YLiKy1qBAXKCxVk3akggiaU2atz7upTCa1WyW3ViWp4Q46KxfftZ"
                    },
                    "coin": {
                        "locked": 14588009793,
                        "price": 597031840,
                        "supply": 24434224128,
                        "watermark": 38438992674
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsWGqbjBrnb",
                        "description": "Value BitClout Investor.\nFrom \ud83c\udde8\ud83c\udded\nI will give away a one-way ticket to Antarctica among my subscribers \u2708\ufe0f\np.s. Sorry for my awful english.",
                        "height": 7655,
                        "is_hidden": 0,
                        "reward_points": 1100,
                        "stake_points": 12500,
                        "username": "pingu_venture"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 6557,
                        "pubkey": "BC1YLiKy1qBAXKCxVk3akggiaU2atz7upTCa1WyW3ViWp4Q46KxfftZ"
                    },
                    "coin": {
                        "locked": 14588009793,
                        "price": 597031840,
                        "supply": 24434224128,
                        "watermark": 38438992674
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsWGqbjBrnb",
                        "description": "Value BitClout Investor.\nFrom \ud83c\udde8\ud83c\udded\nI will give away a one-way ticket to Antarctica among my subscribers \u2708\ufe0f\np.s. Sorry for my awful english.",
                        "height": 7655,
                        "is_hidden": 0,
                        "reward_points": 1100,
                        "stake_points": 12500,
                        "username": "pingu_venture"
                    }
                }
            },
            {
                "diamond": {
                    "level": 1,
                    "value": 50000
                },
                "post": {
                    "account": {
                        "height": 9977,
                        "pubkey": "BC1YLga4HDxYaQbcSUJpg5dNqe5Mv4a9qKSxS3K28kLFT7ERse7yUcq"
                    },
                    "coin": {
                        "locked": 6574120736,
                        "price": 350933828,
                        "supply": 18733220353,
                        "watermark": 24568140092
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/RLfZySCbu1y",
                        "description": "GMBAds\u269c\ufe0fMarketing \nTorts Law Start-Up\u2696\ufe0f\nDad\ud83d\udc68\u200d\ud83d\udc66\u2693\ufe0f\n\u041e\u0434\u0435\u0441\u0441\u0430 \ud83c\uddfa\ud83c\udde6\ud83d\udccdNew York\ud83d\uddfd\nAds Soho BitClout Art NFT House \ud83d\udc8e\ud83e\udd32\ud83d\udd79\n11%FR\nBit All Day Clout All Night @BitCloutLabs",
                        "height": 9979,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "GeneGMB"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 9977,
                        "pubkey": "BC1YLga4HDxYaQbcSUJpg5dNqe5Mv4a9qKSxS3K28kLFT7ERse7yUcq"
                    },
                    "coin": {
                        "locked": 6574120736,
                        "price": 350933828,
                        "supply": 18733220353,
                        "watermark": 24568140092
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/RLfZySCbu1y",
                        "description": "GMBAds\u269c\ufe0fMarketing \nTorts Law Start-Up\u2696\ufe0f\nDad\ud83d\udc68\u200d\ud83d\udc66\u2693\ufe0f\n\u041e\u0434\u0435\u0441\u0441\u0430 \ud83c\uddfa\ud83c\udde6\ud83d\udccdNew York\ud83d\uddfd\nAds Soho BitClout Art NFT House \ud83d\udc8e\ud83e\udd32\ud83d\udd79\n11%FR\nBit All Day Clout All Night @BitCloutLabs",
                        "height": 9979,
                        "is_hidden": 0,
                        "reward_points": 1111,
                        "stake_points": 12500,
                        "username": "GeneGMB"
                    }
                }
            },
            {
                "diamond": {
                    "level": 1,
                    "value": 50000
                },
                "post": {
                    "account": {
                        "height": 10081,
                        "pubkey": "BC1YLgdWqLHmMH4iuGsdGnC1xXUUSNNqRqwPLpVNC14GxQDQp9DUuyf"
                    },
                    "coin": {
                        "locked": 1068357607,
                        "price": 104506794,
                        "supply": 10222853107,
                        "watermark": 13438450504
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/WgzVxiV14ab",
                        "description": "Keeping it pure. Asker of good questions. Finder of beautiful and sometimes hilarious things. Examiner of life up close and from unusual angles. 8% founder's fee. \u267e",
                        "height": 10082,
                        "is_hidden": 0,
                        "reward_points": 800,
                        "stake_points": 12500,
                        "username": "Fireweed"
                    }
                },
                "receiver": {
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx"
                    },
                    "coin": {
                        "locked": 2612356540128,
                        "price": 18968013019,
                        "supply": 137724311839,
                        "watermark": 255810788786
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8Q8SSnZ6F",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6044,
                        "is_hidden": 0,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "username": "diamondhands"
                    }
                },
                "sender": {
                    "account": {
                        "height": 10081,
                        "pubkey": "BC1YLgdWqLHmMH4iuGsdGnC1xXUUSNNqRqwPLpVNC14GxQDQp9DUuyf"
                    },
                    "coin": {
                        "locked": 1068357607,
                        "price": 104506794,
                        "supply": 10222853107,
                        "watermark": 13438450504
                    },
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/WgzVxiV14ab",
                        "description": "Keeping it pure. Asker of good questions. Finder of beautiful and sometimes hilarious things. Examiner of life up close and from unusual angles. 8% founder's fee. \u267e",
                        "height": 10082,
                        "is_hidden": 0,
                        "reward_points": 800,
                        "stake_points": 12500,
                        "username": "Fireweed"
                    }
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}
