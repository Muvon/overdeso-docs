---
description: Here is information about how API requests built and what concept do we use.
---

# ⚙ API concept

## Single API endpoint

We use single API endpoint to access all available actions. The query to the API should be **POST** and contain **JSON** as request data.

The **URL** to send requests is – **https://api.overdeso.com/v1/**

Where is **v1** is version of API. While we are still in development and early access mode its always v1.

{% hint style="danger" %}
**Attention!**  While we are in active development we offer 2 API endpoints: **api1** and **api2**. So basically it means that there are 2 URLs: **https://api1.overdeso.com/v1/** and **https://api2.overdeso.com/v1/.**

We use it one by one on each update. For example, we deployed new version on api1. It becomes active. Next we work and prepare update with new docs and breaking changing and deploy to api2. So devs have time even in active development stage to update their apps and move to another endpoint without breaking things.&#x20;

<mark style="color:orange;">**👉 Current doc version API: api2**</mark>&#x20;

**P.S.** **api.overdeso.com** points to latest released update

**P.P.S.** we deploy updates weekly on **Mondays**, but sometimes more often :)
{% endhint %}

You can pass **X-Account-Pubkey** in header to get reader state in various of methods.

{% hint style="info" %}
The API is fully open to public now but in future releases you need to pass your personal token in header **X-API-Token**, but we will update docs later.
{% endhint %}

**JSON** data is a simple list with methods to process and params for each method. That means if you want to query for one method just simply send one request in list. Lets look on example.

```json
[
    {
        "method": "block.get",
        "params": {
            "height": 1
        }
    },
    {
        "method": "block:get",
        "params": {
            "height": 123123123123123123
        }
    }
]
```

You can see list of structs each contains **method** and **params**. Each method has own params set. To find out just go to method API documentation and check it there.

The response is also unified. You get same indexed list with results for each of your requests in payload body. Each result has structure of a simple list where error comes first and response result second. Lets check example.

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
            "tx_count": 1,
            "txs": [
                "3JuETkEpP92uwnvTDYvhB5uSyAXqG8fDBaUA9UasAijChf3ZAkUPDT"
            ]
        }
    ],
    [
        "error",
        "Block not found"
    ]
]
```

Simply check first element of list and if its null – we got results! If it contains eror code that mean that we can check error details in second element of list.&#x20;

So here we got response with 2 results for our 2 requests. And first one succeed but second one failed. The **HTTP** code of such response is always **200**.

There is case when things go wrong and no one of requests can be processed. For example you send GET instead of POST or just wrong request body. In that cases you will get non-OK (not 200) HTTP code in header and body with extra info about error that follows same rules – 1st index error code, 2nd error descritption.

Now you can go to check what methods we support and try to request the API. Lets go!
