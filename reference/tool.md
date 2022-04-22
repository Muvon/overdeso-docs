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

### tool.article

Prepare article to get published and get overdeso protocol for it's transaction.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>article</td><td></td><td>true</td><td>HTML body of the article</td></tr></tbody></table>

#### Response

Return filtered `article` HTML and `overdeso` protocol in hex to use for submitting transaction.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"tool.article","params":{"article": "<div><div><div><h2>heading 2\n\n<\/h2><h3>heading 3<\/h3><div><br><\/div><blockquote>some test for list:<\/blockquote><ul><li>list 1<\/li><li><b>list 2<\/b><\/li><li>list 3<\/li><\/ul><div><strike>line<\/strike><\/div><div><br><\/div><div><a href=\"12312312312\">tdada its a link<\/a><\/div><div><br><\/div><div class=\"\">its a test\n\n<img src=\"https:\/\/images.deso.org\/5bcdf081b3041513e71e863084075cdff8ea2c8c7bf542c8c0e00464b66f8f15.webp\"><br>\n<\/div><\/div><\/div><\/div>"}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "html": "<div><div><div><h2>heading 2\n\n</h2><h3>heading 3</h3><div></div><blockquote>some test for list:</blockquote><ul><li>list 1</li><li><b>list 2</b></li><li>list 3</li></ul><div><strike>line</strike></div><div></div><div><a href=\"12312312312\">tdada its a link</a></div><div></div><div>its a test\n\n<img src=\"https://images.deso.org/5bcdf081b3041513e71e863084075cdff8ea2c8c7bf542c8c0e00464b66f8f15.webp\">\n</div></div></div></div>",
            "protocol": "0100030300a7033c6469763e3c6469763e3c6469763e3c68323e68656164696e6720320a0a3c2f68323e3c68333e68656164696e6720333c2f68333e3c6469763e3c2f6469763e3c626c6f636b71756f74653e736f6d65207465737420666f72206c6973743a3c2f626c6f636b71756f74653e3c756c3e3c6c693e6c69737420313c2f6c693e3c6c693e3c623e6c69737420323c2f623e3c2f6c693e3c6c693e6c69737420333c2f6c693e3c2f756c3e3c6469763e3c737472696b653e6c696e653c2f737472696b653e3c2f6469763e3c6469763e3c2f6469763e3c6469763e3c6120687265663d223132333132333132333132223e7464616461206974732061206c696e6b3c2f613e3c2f6469763e3c6469763e3c2f6469763e3c6469763e697473206120746573740a0a3c696d67207372633d2268747470733a2f2f696d616765732e6465736f2e6f72672f356263646630383162333034313531336537316538363330383430373563646666386561326338633762663534326338633065303034363462363666386631352e77656270223e0a3c2f6469763e3c2f6469763e3c2f6469763e3c2f6469763e"
        }
    ]
]
```
{% endtab %}
{% endtabs %}

