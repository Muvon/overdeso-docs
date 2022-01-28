---
description: Extra tools to build with ease
---

# 🛠 Tool

### tool.opengraph

Get link preview from og:\* meta data using site URL.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>url</td><td></td><td>true</td><td>URL of page to fetch it for</td></tr></tbody></table>

#### Response

Returns structured info parsed from meta tags for opengraph.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"tool.opengraph", "params": {"url":"https://deso.org"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "title": "Deso | The Decentralized Social Blockchain",
            "image": "https://uploads-ssl.webflow.com/6148aea00f7f90ad88e373a0/6149f799528858b90d4a34c8_Frame%2039864%20(1).jpg"
        }
    ]
]
```
{% endtab %}
{% endtabs %}
