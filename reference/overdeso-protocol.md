---
description: >-
  This page describes technical documentation of Overdeso protocol that extends
  DeSo social functionality.
---

# 🚀 Overdeso protocol

### Concept

{% hint style="danger" %}
Work in progress. We can change protocol description any time before we release it.&#x20;

Take a notice that the protocol is still in the mode of creating.
{% endhint %}

Overdeso protocol utilizes `extra data` of transaction. To make it easier and to protect from intersections with **DeSo** protocol changes we have decided to use single field of extra data with name of `overdeso`. This field is encoded in special format. Each type of transaction has its own allowed fields that are encoded and also updated as of per blockchain indexing.

`overdeso` **protocol of version 1** keys built as follows:

1. **1 byte** protocol version (now is 1);
2. **1 byte** keymap ID (each tx type can have maximum 255 keys);
3. Compressed value depending on its type.

**Unsigned int, integer, bool** are encoded as variable int using DeSo core lib logic.

**String** encoded as follows

* **N bytes** of value for defined key;
* **1 byte** flag if its compressed or not;
* Binary value for the data of the key.

**String** types of value are compressed by **lz4** in case if compressed flag passed.

**List** represents string type but with special encoded way. List items encoded as follows:

* **N bytes** of total value for defined key;
* **1 byte** flag if its compressed or not;
* **List** of items separated with **\0.**

**Enum** is **string** type but has limited values to be set in it using validation, simply one of.

If data encoded in wrong way the indexer is simply ignoring it as no data at all. So only valid data in `overdeso` key are processed and indexes as per transaction basis.

### Keymap

Each transaction type has its own predefined keymap.

Base type for `enum` and `URL` is `string`.&#x20;

#### UPDATE\_PROFILE

<table><thead><tr><th>Index</th><th>Field name</th><th data-type="select">Field type</th><th>Description</th></tr></thead><tbody><tr><td><code>0</code></td><td><code>first_name</code></td><td></td><td>Validation: <code>[^ ]+</code></td></tr><tr><td><code>1</code></td><td><code>last_name</code></td><td></td><td>Validation <code>[^ ]+</code></td></tr><tr><td><code>2</code></td><td><code>gender</code></td><td></td><td>One of: n, m, f<br>n - none<br>m - male<br>f - female</td></tr><tr><td><code>3</code></td><td><code>birth_date</code></td><td></td><td>Date of birth</td></tr><tr><td><code>4</code></td><td><code>instagram</code></td><td></td><td>Instagam profile.<br>Validation: <code>(?:(?:http|https)://)?(?:www.)?(?:instagram.com|instagr.am|instagr.com)/(\w+)</code></td></tr><tr><td><code>5</code></td><td><code>facebook</code></td><td></td><td>Facebook profile.<br>Validation: <code>(?:(?:http|https)://)?(?:www.)?facebook.com/(?:(?:\w)#!/)?(?:pages/)?(?:[?\w-]/)?(?:profile.php?id=(?=\d.))?([\w-])?</code></td></tr><tr><td><code>6</code></td><td><code>medium</code></td><td></td><td>Medium profile.<br>Validation: <code>(?:https?:)?//medium.com/(?:(?:@(?P[A-z0-9]+))|(?P[a-z-]+))/(?P[a-z0-9-]+)-(?P&#x3C;post_id>[A-z0-9]+)(?:?.*)?</code></td></tr><tr><td><code>7</code></td><td><code>github</code></td><td></td><td>Github profile.<br>Validation: <code>(?:https?:)?//(?:www.)?github.com/(?P[A-z0-9_-]+)/?</code></td></tr><tr><td><code>8</code></td><td><code>twitter</code></td><td></td><td>Twitter profile. <br>Validation: <code>(?:https?:)?//(?:[A-z]+.)?twitter.com/@?(?!home|share|privacy|tos)(?P[A-z0-9_]+)/?</code></td></tr><tr><td><code>9</code></td><td><code>telegram</code></td><td></td><td>Telegram messanger profile. Validation: <code>(?:https?:)?//(?:t(?:elegram)?.me|telegram.org)/(?P[a-z0-9_]{5,32})/?</code></td></tr><tr><td><code>10</code></td><td><code>linkedin</code></td><td></td><td>Linkedin profile.<br>Validation: <code>(?:https?:)?//(?:[\w]+.)?linkedin.com/in/(?P[\w-_À-ÿ%]+)/?</code></td></tr><tr><td><code>11</code></td><td><code>snapchat</code></td><td></td><td>Snapshat profile link.<br>Validation: <code>(?:https?:)?//(?:www.)?snapchat.com/add/(?P[A-z0-9._-]+)/?</code></td></tr><tr><td><code>12</code></td><td><code>reddit</code></td><td></td><td>Reddit profile.<br>Validation: <code>(?:https?:)?//(?:[a-z]+.)?reddit.com/(?:u(?:ser)?)/(?P[A-z0-9-_]*)/?</code></td></tr><tr><td><code>13</code></td><td><code>angellist</code></td><td></td><td>Angellist profile. Validation: <code>(?:https?:)?//angel.co/(?Pu|p)/(?P[A-z0-9_-]+)</code></td></tr><tr><td><code>14</code></td><td><code>crunchbase</code></td><td></td><td>Crunchbase profile.<br>Validation: <code>(?:https?:)?//crunchbase.com/person/(?P[A-z0-9_-]+)</code></td></tr><tr><td><code>15</code></td><td><code>vk</code></td><td></td><td>VK profile.<br>Validation: <code>(?:https?:)//(www.)?(vk.com/)(id\d|[a-zA-z][a-zA-Z0-9_.]{2,})</code></td></tr><tr><td><code>16</code></td><td><code>tagging</code></td><td></td><td>Who can tag you to make you receive notifications of those posts.<br>One of: any, following, nobody</td></tr><tr><td><code>17</code></td><td><code>country</code></td><td></td><td>2-letter country code in lower case</td></tr><tr><td><code>18</code></td><td><code>language</code></td><td></td><td>2-letter language code in lower case</td></tr></tbody></table>

#### SUBMIT\_POST

<table><thead><tr><th>Index</th><th>Field name</th><th data-type="select">Field type</th><th>Description</th></tr></thead><tbody><tr><td><code>0</code></td><td><code>type</code></td><td></td><td>One of: story, live or poll.<br><code>story</code> – means the post contains video/image for story.<br><code>live</code> – means the post contains livestream or recorded video to it if it was in past.<br><code>poll</code> – means you have options in data.</td></tr><tr><td><code>1</code></td><td><code>options</code></td><td></td><td>List of options for defined poll. Options cannot be reordered on update poll and only added new.</td></tr><tr><td>2</td><td><code>category</code></td><td></td><td>Customize feed category for this post. Follows validation of hashtags</td></tr></tbody></table>

#### LIKE

<table><thead><tr><th>Index</th><th>Field name</th><th data-type="select">Field type</th><th>Description</th></tr></thead><tbody><tr><td><code>0</code></td><td><code>emoji</code></td><td></td><td>Contains emoji reaction to this like. Can be used only on like and skipped on unlike.<br>Validation: <code>([0-9#][\x{20E3}])|[\x{00ae}\x{00a9}\x{203C}\x{2047}\x{2048}\x{2049}\x{3030}\x{303D}\x{2139}\x{2122}\x{3297}\x{3299}][\x{FE00}-\x{FEFF}]?|[\x{2190}-\x{21FF}][\x{FE00}-\x{FEFF}]?|[\x{2300}-\x{23FF}][\x{FE00}-\x{FEFF}]?|[\x{2460}-\x{24FF}][\x{FE00}-\x{FEFF}]?|[\x{25A0}-\x{25FF}][\x{FE00}-\x{FEFF}]?|[\x{2600}-\x{27BF}][\x{FE00}-\x{FEFF}]?|[\x{2900}-\x{297F}][\x{FE00}-\x{FEFF}]?|[\x{2B00}-\x{2BF0}][\x{FE00}-\x{FEFF}]?|[\x{1F000}-\x{1F6FF}][\x{FE00}-\x{FEFF}]?</code></td></tr><tr><td></td><td></td><td></td><td></td></tr></tbody></table>

#### Something else?  (NOT YET USED)

<table><thead><tr><th>Index</th><th>Field name</th><th data-type="select">Field type</th><th>Description</th></tr></thead><tbody><tr><td><code>0</code></td><td><code>first_name</code></td><td></td><td>Validation: <code>[^ ]+</code></td></tr></tbody></table>
