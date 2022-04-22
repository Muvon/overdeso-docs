---
description: Post related API methods.
---

# 📄 Post

### post.get

Fetch post by its hash and optionally fetch related comments to it.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr></tbody></table>

#### Response

The method returns post information and related comments to it if requested

**author** – information about account who created that post.

**parent** - post structure of parent post if have.

**root** - post structure of root post if have.

**post** - information about requested post.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"post.get", "params": {"hash":"75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4"}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "depth": 0,
            "is_quoted": false,
            "text": "In retrospect, it was inevitable",
            "lang": null,
            "has_media": false,
            "has_image": false,
            "has_video": false,
            "media": {
                "image_urls": []
            },
            "is_hidden": false,
            "is_nft": true,
            "submitted_at": 1615574830,
            "nft": {
                "is_selling": 1,
                "has_unlockable": 0,
                "nft_count": 1,
                "creator_royalty": 0,
                "coin_royalty": 1500
            },
            "stat": {
                "last_stat_ts": 1641223938,
                "like_count": 311,
                "diamond_count": 16721,
                "diamond_value": 20644876649,
                "repost_count": 36,
                "quote_count": 29,
                "comment_count": 87,
                "nft_bid_count": 0,
                "nft_trade_count": 0,
                "nft_burned_count": 0
            },
            "hash": "75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4",
            "root": null,
            "parent": null,
            "repost": null,
            "account": {
                "height": 6042,
                "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                "balance": 1202813160669,
                "timestamp": 1615574505,
                "profile": {
                    "timestamp": 1615574830,
                    "is_hidden": false,
                    "height": 6043,
                    "username": "diamondhands",
                    "description": "💎🙌",
                    "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                    "reward_points": 0,
                    "stake_points": 12500
                },
                "coin": {
                    "supply": 164216917444,
                    "locked": 4578658488257,
                    "watermark": 255810788786,
                    "price": 27881771010
                }
            }
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.article.get

Fetch HTML formatted article for post hash in case if this post is article.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr></tbody></table>

#### Response

The method returns plain text of article in HTML format.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"post.article.get", "params": {"hash":"49c7e9b9dc4c11cb9ddf93d7b2519754ac3a9c17d7bb083d20ca33b0163a6b30"}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        "<div><div><div><div><h2>Heading 2</h2><p>i hope its paragraph and not a divdd</p><p>Nad its a list:</p><div><p></p><ul><li>list 1</li><li>list2</li><li>list3</li></ul><p></p></div><div><p>aand it's an image:</p><img src=\"https://images.deso.org/5bcdf081b3041513e71e863084075cdff8ea2c8c7bf542c8c0e00464b66f8f15.webp\"></div><div></div></div></div></div></div>"
    ]
]
```
{% endtab %}
{% endtabs %}

### post.list

Return recent list of newly created posts without any reposts.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>false</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>type</td><td></td><td>false</td><td>Filter posts by its type. Can be one of: <code>post</code>, <code>repost</code>, <code>quote</code>, <code>story</code>, <code>live</code>, <code>poll</code>, <code>article</code>.<br>It's not specified by default in case account passed.<br>It has default value <code>post</code> for no acount specified requests.</td></tr><tr><td>lang</td><td></td><td>false</td><td>Languge code to fetch. Default is null so means any language</td></tr><tr><td>has_media</td><td></td><td>false</td><td>Fetch posts that have media only</td></tr><tr><td>has_video</td><td></td><td>false</td><td>Fetch posts that have video only</td></tr><tr><td>has_image</td><td></td><td>false</td><td>Fetch posts that have image only attached to it</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Return latest posts for network or for account if passed in request.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.list", "params": {"lang": "en", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1
```

```json
[
    [
        null,
        {
            "count": 2310116,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "🔥 13 years ago Satoshi Nakamoto created the genesis block of bitcoin\n\nIn block 0, Satoshi indicated the text from the headline of The Times: \"The Times 03 / Jan / 2009 Chancellor on brink of second bailout for banks\".\n\nThe first block generated 50 BTC. Then their price was $ 0.00. On July 17, 2010, there was a demand for cue ball and the price rose to $ 0.09.\n\nSince then, BTC has grown by 52.2 million percent 🚀\n",
                    "lang": "en",
                    "has_media": true,
                    "has_image": true,
                    "has_video": false,
                    "media": {
                        "image_urls": [
                            "https://images.deso.org/912d229bdb37432b326b175b5606d0d5d60f9935db86f73e841dcae34798b7fd.webp"
                        ]
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1641225316,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 0,
                        "like_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "hash": "e1494f2839b98effa5c74c739ce2a630a41d58f1d5886bb4feafff63ec63d524",
                    "repost": null,
                    "account": {
                        "height": 44467,
                        "pubkey": "BC1YLfovdgWCbAdkRMX7W5igjhuirVrY1zRvmd5zPVjCn5DuvcmgSQh",
                        "balance": 5799801180,
                        "timestamp": 1626850074,
                        "profile": {
                            "timestamp": 1629826298,
                            "is_hidden": false,
                            "height": 54404,
                            "username": "90Degree",
                            "description": "Your daily update on \nCrypto and NFT News",
                            "avatar_url": "https://overdeso.com/media/avatar/Vh1etMK6oXw",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 16809167440,
                            "locked": 4749402584,
                            "watermark": 19317114377,
                            "price": 282548353
                        }
                    },
                    "state": {
                        "is_liked": false,
                        "diamond_level": 0
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "some NYC #streetphotography for the @PhotographersCorner contest\n\nPosted via @cloutfeed",
                    "lang": "en",
                    "has_media": true,
                    "has_image": true,
                    "has_video": false,
                    "media": {
                        "image_urls": [
                            "https://images.deso.org/b1cb798da53da0ec567b47eb422e31171f1eef10100efa9ddb10eee075c0efc0.webp"
                        ]
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1641225316,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 0,
                        "like_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "hash": "6429bb0305462db28dba147bb3048add539abcba091aca95b35b5bbfd62b4446",
                    "repost": null,
                    "account": {
                        "height": 41364,
                        "pubkey": "BC1YLhbYNnu9wxmPuT4xmdi3sCshgU3cS1ZqzjRv8P5kpqtKBZxBnzR",
                        "balance": 323874398,
                        "timestamp": 1625921846,
                        "profile": {
                            "timestamp": 1625921846,
                            "is_hidden": false,
                            "height": 41363,
                            "username": "almostgreat",
                            "description": "home after picking up cigarettes and milk. now sharing and selling some of my old photos. \n\ncommunity at ardrive.io\n\n🛒 almostgreatco.etsy.com",
                            "avatar_url": "https://overdeso.com/media/avatar/UMB5qyP9WVP",
                            "reward_points": 2000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 9279501171,
                            "locked": 799050340,
                            "watermark": 9323560621,
                            "price": 86109191
                        }
                    },
                    "state": {
                        "is_liked": false,
                        "diamond_level": 0
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.hot.list

Return feed with hot posts aggregated by custom rules and engagement.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of posts

#### Examples

{% tabs %}
{% tab title="First Tab" %}
```shell
curl -s --data '[{"method":"post.hot.list", "params": {"offset": 0, "limit": 2}}]' https://api.overdeso.com/v1
```

```json
[
    [
        null,
        {
            "count": 624,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "Just some Statistics:\n\n📺 We've made 266 Daily Videos thus far. \n\n📺 We've had 53 different guests on our show.\n\n📺 We have yet to miss a single day. (There have been 7 episodes in which one of us couldn't be present)\n\n📺 We've recorded from Florida, Turks and Caicos, Minnesota, Wisconsin, Iowa, New York, and even once in our car.\n\n📺 Our videos have been watched 43,300 times for 168,000 minutes.\n \n📺 Our most famous guest was @CaroleBaskin.\n\n📺 The guests with the most appearances are @Tropix and @CyrusAbrahim, followed by @MarioNawfal.\n\n📺 Some of our favorite guests have been @sandirose @mechellLord @designsta @salilsethi @clayperry @doodles @Michaelleerolland @IZY @drkatcohen @reade @chasesteely @matreshka @illumemenati and just about everyone else who appeared!\n\n📺Who we would like to have on our show:  @nader @chamath @alexvalaitis @fastfreddie @Maebeam @MissKatiann and anyone else who’d like to join!\n\n📺 We plan to keep the streak alive as long as we can.  See you all on Day 5700!\n\nPlease Subscribe:  https://www.youtube.com/c/BrianKrassenstein/videos\n\nPosted via @cloutfeed",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1643835505,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1643847979,
                        "like_count": 54,
                        "diamond_count": 48,
                        "diamond_value": 64300000,
                        "repost_count": 12,
                        "quote_count": 5,
                        "comment_count": 26,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "links": null,
                    "hash": "1fe53c7d4cc82383e649357901cd145f74d52e1355dab02dea9a2fa59d9a9a29",
                    "repost": null,
                    "account": {
                        "height": 9262,
                        "pubkey": "BC1YLj3a3xppVPtAoMAzh1FFYtCTiGomjaA5PRcqS1PVRk8KqDw385y",
                        "balance": 250764681927,
                        "timestamp": 1616560138,
                        "profile": {
                            "timestamp": 1616560138,
                            "is_hidden": false,
                            "height": 9261,
                            "username": "Krassenstein",
                            "description": "Krassenstein Twins\n\n✅ Co-Founder @NFTz (NFTz.zone) & @CheckBitClout\n✅ NFT Projects: @BitCloutKids & @NaderHeads\n\nCheck out our NFT collection:  krassenstein.nftz.zone\n\n",
                            "avatar_url": "https://media1.overdeso.com/avatar/XhCYHZgPizx",
                            "reward_points": 990,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 108896662896,
                            "locked": 1301739332785,
                            "watermark": 111627931698,
                            "price": 35861690202
                        },
                        "dao": null
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "*Sneak Peak from @CloutWomenUnite 3D Virtual Gallery progress we are almost ready to roll! really honored to have the opportunity to build this space for our female creators.\n\n*3D sculpture by @ohlala \n\n*NFTs project spotted:\n@NATALIART \n@ClaraMouse \n@Twinsdivisions \n@NonaRivers \n@BoopsBoutique \n@anastasiakhoroshenko \n@All_things_creative \n\n@AlexValaitis @nader @disruptepreneur @Krassenstein \n@MechellLord ",
                    "lang": null,
                    "has_media": true,
                    "has_image": true,
                    "has_video": false,
                    "media": {
                        "image_urls": [
                            "https://images.deso.org/445cced023718a22a930d3bc89e1ccb92eccb9fc4c2c44f1525ba48d063df870.webp"
                        ]
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1643835394,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1643848134,
                        "like_count": 23,
                        "diamond_count": 21,
                        "diamond_value": 5900000,
                        "repost_count": 3,
                        "quote_count": 8,
                        "comment_count": 14,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "links": null,
                    "hash": "481e7706878ee5d6b9436d1b9a90c9b919453b09eb156545f00ef37507dcb8aa",
                    "repost": null,
                    "account": {
                        "height": 34246,
                        "pubkey": "BC1YLiJZXbqJh7o7xxsmJGf6vb3EUBpHCbXcmqyMTUhVmcoEVRxi37m",
                        "balance": 40321654898,
                        "timestamp": 1623785625,
                        "profile": {
                            "timestamp": 1623785625,
                            "is_hidden": false,
                            "height": 34245,
                            "username": "GDvirtualgalleries",
                            "description": "Get your NFT and claim your 3D Virtual Gallery!\nBy @GDS\n\nPart of the 1st cohort of projects for venture investment from DeSo.\n\nOG April 10 👽",
                            "avatar_url": "https://media1.overdeso.com/avatar/S1arcrwYNKf",
                            "reward_points": 4000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 31845708223,
                            "locked": 72666089487,
                            "watermark": 42250991289,
                            "price": 6845452728
                        },
                        "dao": null
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.follow.list

Get posts of followed accounts by requested account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>account</td><td></td><td>false</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns same structure of post.list returns but for followed accounts only.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.list", "params": {"account": "krassenstein", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1
```

```json
[
    [
        null,
        {
            "count": 3382,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "Welcome to Deso!\nA few tips for new users:\n\n❇️ List of nodes DeSo.Directory.\n\nMobile apps:\n\n❇️@CloutFeed app for a great mobile experience of DeSo\n❇️@Cloutie A BitClout app for iOS & Mac OS.\n\nCreator Coin Etiquette framework.\ndocs.google.com/document/d/1SVelAUittP-QemhyZdRIQa8sReDl5YKhC-mapc5BPRg/edit\n\n❇️Popular nodes:\n@tijn.club, @nachoaverage.com,\n🌺diamondapp.com/notifications\n🌺desocialworld.com (supports different languages)\n\n❇️keyword search tool\n🌺@SearchClout\n\n❇️To see interesting data like Creators activity in and new users joining DeSo\n🌺@AltumBase\n\n❇️To find work/collaborate with creators or to offer your services:\n🌺@CreaTiers creatiers.co\n\n❇️Monetize your account through:\n🌺CloutCast (Also integrated in CloutFeed)\n🌺ADClouts -Promote your posts, reach a wide audience\n\n❇️NFT focused:\n\n🌸@Supernovas.app\n🌸@Polygram.cc\n🌸NFTs.zone\n🌸 stetnode.com\n\n❇️@OpenProsper| Track, analyze and discover creator coins.\n❇️@Pulse Bitcloutpulse.com Stay ahead of the curve and track the hottest creator coins on BitClout with BitClout Pulse\n\n❇️Cool Tools\n\n🌸bitclout.plus Changes 280 character limit to be 10000 on new posts; Username autocomplete\n\n🌸@cordify cordify.app Cordify enables you to interact with DeSo blockchain, send or receive $DeSo tippings (aka diamonds 💎)\n\n🌸@oneclout OneClout sends your BC posts to your TW\n\n❇️Clubhouse rooms!\n\n🌸Music Monday 8 am pst\n🌸Ladies on Mic\n\nclubhouse.com/event/MO6DaLGQ\n\n🌸Deso week review\n🌸What Deso?\n\n❇️Clubs to follow:\nBitclout Chats/Deso Chats\nBitclout users\nCloutwomenunite\nDeso shill @ Chill\nThink Different NFT\nDeso Music NFTS\n\n❇️Discord groups:\n\n💎Join the DeSo Discord to stay up to date, link on Twitter: @DesoProtocol(discord.gg/deso)\n💎 DesoFoundation\n💎 Deso NFTs\n💎 Deso Voices\n\nTelegram channels:\n\n💎The DeSo Spanish Club\n💎NFTplace on Bitclout\n💎DeSo Creators\n💎Bitclout World\n\n❇️Women Focused Telegram:\n❤️Bitclout OG Women\n\n❇️Accounts supporting female creators:\n🌺@Cloutwomenunite\n🌺@Globalwomen\n🌺@TheCreateherInitiative\n\n❤️Women of Bitclout directory: clout.link/oclm0ox (please enter your information)\n\nTo organize meetups/sessions\n🌺@JamClout\n🌺@Chime-in\n🌺@CloutVid\n🌺Twitter spaces\n🌺Discord\n\n❇️To schedule a clubhouse room with community :\n\n🌺Bitclout chats/Deso chats (@DeSoChats)\n🌺@ThinkDifferent\n🌺@CloutWomenUnite\n\nPeople/Accounts to Follow:\n\n❇️ Core Team Community representatives:\n@nader @AlexValaitis @meghanvita @FastFreddie\n\n❇️Follow @Krassenstein, the most active account on DeSo always with very valuable content\n\n❇️Follow @BitsTODAY A nightly digest of everything happening in the world of clout.READ: bit.ly/bcbits\n❇️@BitActive team will help to share your content\n\n❇️Community builders to Follow:\n@Izy @Matreshka @MissKatian @darian_parrish @SpunkArt @MechellLord @GDS @mashelenn @FrenchConnector @NATALIART @CloutWomenUnite @GlobalWomen @SavingTheSurvivors\n@Designsta\n\n❇️Musicians:\n🌺@Goldberry @Murkury @DOZ @Tropix @ClayPerryMusic\n\n❇️Keepin’ It Real:\n🌺@Sandirose @HPaulson @JDArmstrong",
                    "lang": "en",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1643354602,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 0,
                        "like_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "hash": "560f3221dcdb7f649f8d306996f30c9f25663747651efa592dffccd22d50e6ad",
                    "repost": {
                        "depth": 0,
                        "is_quoted": false,
                        "text": "It's time to DESO! ",
                        "lang": "pt",
                        "has_media": false,
                        "has_image": false,
                        "has_video": false,
                        "media": null,
                        "is_hidden": false,
                        "is_nft": false,
                        "submitted_at": 1643353893,
                        "hash": "3dfc1560a85a6bd60522de5e7eb9dd1218bb04e4165c2d262dcb3a92974eeb52",
                        "account": {
                            "height": null,
                            "pubkey": "BC1YLiZtnb2q1dM6xF78Mho4HmqWZzsy3YDjSj1FssXFsLSUCdRZYP2",
                            "balance": 2080223454,
                            "timestamp": 1643352685,
                            "profile": {
                                "timestamp": 1643353596,
                                "is_hidden": false,
                                "height": 99182,
                                "username": "GoddessHighConnections333",
                                "description": "💋✨High Connections Elevations ✨💋",
                                "avatar_url": "http://media.overdeso.lo/avatar/XMqPbif42hQ",
                                "reward_points": 1000,
                                "stake_points": 12500
                            },
                            "coin": {
                                "supply": 2955589975,
                                "locked": 25818598,
                                "watermark": 2955589975,
                                "price": 26206545
                            },
                            "dao": null
                        }
                    },
                    "account": {
                        "height": 27159,
                        "pubkey": "BC1YLjTPoBX5Ajma3yaMLUnMfjsYvErtT6v18NQ467MdpohhXSDuQ5T",
                        "balance": 2132231070,
                        "timestamp": 1621804016,
                        "profile": {
                            "timestamp": 1621804016,
                            "is_hidden": false,
                            "height": 27158,
                            "username": "CloutWomenUnite",
                            "description": "This account is about women creators! We onboard, we invest, we create visibility. We use FR and proceeds from NFT sales to reinvested into female creators! \nFounder: BeverageCurator\nCommunity project: @ThecreateHERinitiative\nNFT Project: NFTRU\nPosts posted on the @CloutWomenUnite/DesoWomenUnite wall may be duplicated on our Instagram/Twitter account.\ninstagram.com/cloutwomenunite\n\n@CloutWomenUnite aka @DesoWomenUnite reserves the right to publish selective posts. ",
                            "avatar_url": "http://media.overdeso.lo/avatar/XhK8hNHqVvp",
                            "reward_points": 3000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 14051480681,
                            "locked": 3335813380,
                            "watermark": 19454411635,
                            "price": 712198334
                        },
                        "dao": {
                            "disabled": false,
                            "restriction": 0,
                            "supply": "174876e800"
                        }
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1643354176,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 0,
                        "like_count": 0,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "hash": "ecb40e9f8c05d71bfc741ae40bf778c70aec6442a8b533ad7f0959ff64f58b99",
                    "repost": {
                        "depth": 0,
                        "is_quoted": false,
                        "text": "Tonights winner of Micro-Influencer of the Week is @DannyWithAlotOfUgene. He is our first 3x and 4x winner of the coveted trophy. Back to back winner.\n\nCongrats Danny!",
                        "lang": "en",
                        "has_media": false,
                        "has_image": false,
                        "has_video": false,
                        "media": null,
                        "is_hidden": false,
                        "is_nft": false,
                        "submitted_at": 1643347733,
                        "hash": "93f2b63e3ab8a34ca672c40876dda13eacb6f78583752ac0efab73c27458874d",
                        "account": {
                            "height": 25924,
                            "pubkey": "BC1YLhwowKXkLUFZTexr1j37jgNDTJVm5n93FiRzZ5xark1yt31vWUW",
                            "balance": 1053093299,
                            "timestamp": 1621463747,
                            "profile": {
                                "timestamp": 1621463747,
                                "is_hidden": false,
                                "height": 25923,
                                "username": "streamclout",
                                "description": "BitClout's FIRST native live streaming show!\nMeme battles every Thurs @ 7PM PST\n\nHosts: @brockpierson @LiftClout\n\nA Brock4Prez.com Media Corp\n\nSUB 👇\nhttps://twitch.tv/streamclout",
                                "avatar_url": "http://media.overdeso.lo/avatar/h4aoNhTMFhz",
                                "reward_points": 10000,
                                "stake_points": 12500
                            },
                            "coin": {
                                "supply": 13141160020,
                                "locked": 2269349592,
                                "watermark": 13141160020,
                                "price": 518070660
                            },
                            "dao": null
                        }
                    },
                    "account": {
                        "height": 1470,
                        "pubkey": "BC1YLiCXkGWXdizHXSr1f3E1zoi5oQbtXgiXaHtJP3cVBmgfQFmhVsj",
                        "balance": 6497583305,
                        "timestamp": 1614605377,
                        "profile": {
                            "timestamp": 1614605377,
                            "is_hidden": false,
                            "height": 1469,
                            "username": "v",
                            "description": "10+ years at Goog. Interested in distributed systems, crypto, high skilled immigrant issues, angel investing. All opinions my own. RC!=endorsement.\n\nIf you have a great idea and need an angel, hit me up. PM: linkedin.com/in/varunso\n\nIf you are a strong engineer and are looking for an opportunity, hit me up for a referral at Goog.\n\nOG 03/21",
                            "avatar_url": "http://media.overdeso.lo/avatar/fj8D6Jk2EMn",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 40176307371,
                            "locked": 64850076779,
                            "watermark": 59284350067,
                            "price": 4842412419
                        },
                        "dao": null
                    }
                }
            ]
        }
    ]
]JSON
```
{% endtab %}
{% endtabs %}

### post.highlight.list

Get highlighted posts to show up to attract attention to users who are most engagement by its posts.

#### Request params

This method does not require any params.

#### Response

Returns list of 5 posts that are highlighted

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.highlight.list"]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "depth": 0,
                "is_quoted": false,
                "text": "follow me \n\nthanks 😊",
                "lang": null,
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1645093204,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1645093231,
                    "like_count": 8,
                    "diamond_count": 4,
                    "diamond_value": 5050000,
                    "repost_count": 3,
                    "quote_count": 0,
                    "comment_count": 0,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "links": null,
                "hash": "db02ed455759fab6432834d2b5dd44468601d3387fdca7cdbe0bd8db2e1d8ad6",
                "account": {
                    "height": 15015,
                    "pubkey": "BC1YLh3EUCrzfndGvA2AMnCYbrXzKr3xautJiMoxdGUsQfX3vaaRDWv",
                    "balance": 6479037679,
                    "timestamp": 1618299687,
                    "profile": {
                        "timestamp": 1618455961,
                        "is_hidden": false,
                        "height": 15554,
                        "username": "rhubarb",
                        "description": "basically just red celery",
                        "avatar_url": "http://media.overdeso.lo/avatar/gj4s1nnSR1T",
                        "reward_points": 9969,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 8432353311,
                        "locked": 623908534,
                        "watermark": 27241328748,
                        "price": 221969564
                    },
                    "dao": {
                        "disabled": false,
                        "restriction": 0,
                        "supply": 0
                    }
                }
            },
            {
                "depth": 0,
                "is_quoted": false,
                "text": "Found several hashtags people are using to post interesting content on DeSo.\n\n#nature - https://www.openprosper.com/hashtag/nature\n#science - https://www.openprosper.com/hashtag/science\n#crypto - https://www.openprosper.com/hashtag/crypto\n\nAttaching a post by @BlazingSword with #nature\n",
                "lang": "en",
                "has_media": true,
                "has_image": true,
                "has_video": false,
                "media": {
                    "image_urls": [
                        "https://images.deso.org/4308a07bc8271728440ca1ac6d18f8441561a5d2b1169c41713886fbe31fb617.webp"
                    ]
                },
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1645093734,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1645093742,
                    "like_count": 2,
                    "diamond_count": 3,
                    "diamond_value": 5000000,
                    "repost_count": 1,
                    "quote_count": 0,
                    "comment_count": 0,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "links": [
                    {
                        "image": "https://openprosper-assets.s3.amazonaws.com/images/openprosper-og.jpg",
                        "description": "Advanced DeSo creator insights and analytics. Get DeSo creator coin price, coin holders, wallet, founder reward, and social interaction insights and analytics on OpenProsper.",
                        "title": "DeSo Creator Insights &amp;amp; Analytics | OpenProsper",
                        "url": "https://www.openprosper.com/hashtag/nature"
                    },
                    {
                        "image": "https://openprosper-assets.s3.amazonaws.com/images/openprosper-og.jpg",
                        "description": "Advanced DeSo creator insights and analytics. Get DeSo creator coin price, coin holders, wallet, founder reward, and social interaction insights and analytics on OpenProsper.",
                        "title": "DeSo Creator Insights &amp;amp; Analytics | OpenProsper",
                        "url": "https://www.openprosper.com/hashtag/science"
                    },
                    {
                        "image": "https://openprosper-assets.s3.amazonaws.com/images/openprosper-og.jpg",
                        "description": "Advanced DeSo creator insights and analytics. Get DeSo creator coin price, coin holders, wallet, founder reward, and social interaction insights and analytics on OpenProsper.",
                        "title": "DeSo Creator Insights &amp;amp; Analytics | OpenProsper",
                        "url": "https://www.openprosper.com/hashtag/crypto"
                    }
                ],
                "hash": "896ab8d15196d4ac9ebc2f941f17119f1a58f72dcd7b25803dc14d7ef4364198",
                "account": {
                    "height": 11676,
                    "pubkey": "BC1YLgQkRFM1P3qvW5HQ47cTCikyfB464o4oEbqRkcqJohVs3jfUPib",
                    "balance": 211615195745,
                    "timestamp": 1617293580,
                    "profile": {
                        "timestamp": 1617500092,
                        "is_hidden": false,
                        "height": 12370,
                        "username": "salilsethi",
                        "description": "Creator of @OpenProsper \n\nSee my stats: https://www.openprosper.com/u/salilsethi\n\nFollow to get data-driven creator insights.\n\nMIT and McKinsey alum.",
                        "avatar_url": "http://media.overdeso.lo/avatar/jZzJBwfK6HF",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 40236014873,
                        "locked": 65139635985,
                        "watermark": 56419041768,
                        "price": 4856816166
                    },
                    "dao": null
                }
            },
            {
                "depth": 0,
                "is_quoted": false,
                "text": " ",
                "lang": null,
                "has_media": true,
                "has_image": false,
                "has_video": true,
                "media": {
                    "embed_video_url": "https://w.soundcloud.com/player/?url=https://soundcloud.com/itsjustjohn/are-you-that-somebody-flip?hide_related=true&show_comments=false"
                },
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1645092259,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1645092592,
                    "like_count": 4,
                    "diamond_count": 3,
                    "diamond_value": 150000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 1,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "links": null,
                "hash": "b19043da6a3b48828467b4a15b8d9998623355cf44fefe2298411f6e1d3e97fb",
                "account": {
                    "height": 15015,
                    "pubkey": "BC1YLh3EUCrzfndGvA2AMnCYbrXzKr3xautJiMoxdGUsQfX3vaaRDWv",
                    "balance": 6479037679,
                    "timestamp": 1618299687,
                    "profile": {
                        "timestamp": 1618455961,
                        "is_hidden": false,
                        "height": 15554,
                        "username": "rhubarb",
                        "description": "basically just red celery",
                        "avatar_url": "http://media.overdeso.lo/avatar/gj4s1nnSR1T",
                        "reward_points": 9969,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 8432353311,
                        "locked": 623908534,
                        "watermark": 27241328748,
                        "price": 221969564
                    },
                    "dao": {
                        "disabled": false,
                        "restriction": 0,
                        "supply": 0
                    }
                }
            },
            {
                "depth": 0,
                "is_quoted": false,
                "text": "¡Que el sol salga para todos en este nuevo día y los guíe hacia el camino de la felicidad y el éxito! 😉🤍",
                "lang": null,
                "has_media": true,
                "has_image": true,
                "has_video": false,
                "media": {
                    "image_urls": [
                        "https://images.deso.org/034144c3de166be4845c9006936f0180fa2b5e692c00f00b758500eb08940a48.webp"
                    ]
                },
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1645090946,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1645090998,
                    "like_count": 5,
                    "diamond_count": 3,
                    "diamond_value": 150000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 1,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "links": null,
                "hash": "4a3ad7575c7f9b4d1333a1b654c29e46798dda07930a73dc5245cf48d3c82027",
                "account": {
                    "height": 90038,
                    "pubkey": "BC1YLhe7a9pyL7aTb1z1QjugG23tDPuzqbxgsek2LTooT1Xw9rqkcaa",
                    "balance": 25276895,
                    "timestamp": 1640559426,
                    "profile": {
                        "timestamp": 1640560719,
                        "is_hidden": false,
                        "height": 90039,
                        "username": "marheleosal",
                        "description": "Un día a la vez...\nBirthBlock # 90040 \n26 de diciembre de 2021",
                        "avatar_url": "http://media.overdeso.lo/avatar/cDMtRPr1Htu",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 7843300850,
                        "locked": 482499628,
                        "watermark": 7843300850,
                        "price": 184552276
                    },
                    "dao": null
                }
            },
            {
                "depth": 0,
                "is_quoted": false,
                "text": "True 🤣",
                "lang": null,
                "has_media": true,
                "has_image": true,
                "has_video": false,
                "media": {
                    "image_urls": [
                        "https://images.deso.org/79efcc7ad27c3d8f5d57c65f7dfe4908752e4e697d1a8a20da92c36d13d15345.webp"
                    ]
                },
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1645090946,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1645091131,
                    "like_count": 6,
                    "diamond_count": 3,
                    "diamond_value": 150000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 2,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "links": null,
                "hash": "56c4759d8e86ae4814e1c3e3c5de9c97ab297d7e98e78fc57ba7fa879a52ab14",
                "account": {
                    "height": 32655,
                    "pubkey": "BC1YLheTDZQEJye7tHhFq4gBwbHgxCM9qXvEEEaEFNn3sYysVy6F7MT",
                    "balance": 95300111,
                    "timestamp": 1623222964,
                    "profile": {
                        "timestamp": 1623222964,
                        "is_hidden": false,
                        "height": 32654,
                        "username": "DejanBugi",
                        "description": "Founder of @ItalianChef\n\nLet's spread the magic smell and taste of food. 👌\nElctr. Eng. which passion is cooking(+2y prof.experience abroad)\n✅ @verifiedprofile ➡ bit.ly/3pQVohl",
                        "avatar_url": "http://media.overdeso.lo/avatar/WrtAb5Ekgph",
                        "reward_points": 900,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 6402376656,
                        "locked": 262436274,
                        "watermark": 7424621601,
                        "price": 122971350
                    },
                    "dao": null
                }
            },
            {
                "depth": 0,
                "is_quoted": false,
                "text": "Institutional investors are concentrating 51% of their money in equities. This is the highest level since the dot-com bubble burst",
                "lang": null,
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1645093428,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1645093493,
                    "like_count": 2,
                    "diamond_count": 2,
                    "diamond_value": 100000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 1,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "links": null,
                "hash": "239b2c0ca9d94bab7cffa951c3ba2e87f3fc160d93bce1bc85318db8eef3de56",
                "account": {
                    "height": 76699,
                    "pubkey": "BC1YLhAcB16WSVWeqMuTyRUiRHEQmhm83dcK6YXAwDuF6ipkcdwJMmj",
                    "balance": 350880261,
                    "timestamp": 1636527094,
                    "profile": {
                        "timestamp": 1636684136,
                        "is_hidden": false,
                        "height": 77228,
                        "username": "KINGMETA",
                        "description": "",
                        "avatar_url": "http://media.overdeso.lo/avatar/RqjPdrfhiL1",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 2599457845,
                        "locked": 17565013,
                        "watermark": 5142417499,
                        "price": 20271551
                    },
                    "dao": null
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.story.list

Get recent stories

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of posts that marked as story for latest 3 days.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.story.list", "params": {"offset": 0, "limit": 2}}]' https://api.overdeso.com/v1   | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 0,
            "list": []
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.live.list

Get recent live streams

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of posts that marked as live for latest 3 days.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.live.list", "params": {"offset": 0, "limit": 2}}]' https://api.overdeso.com/v1   | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 0,
            "list": []
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.comment.get

Fetch comment info with full path to the root post.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Comment hash in hex format to fetch</td></tr></tbody></table>

#### Response

The method returns the thread with it's replied related to the passed comment to original post.

**author** – information about account who created that post.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
 curl -s --data '[{"method":"post.comment.get", "params": {"hash":"ae90ff2f644373c1dfc5d3acfa1c07164ab838003def4716e3888837549c1d7a"}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "depth": 0,
                "is_quoted": false,
                "text": "First @elonmusk calls for the decentralization of social, and the open-sourcing of feed algorithms.\n\nNow @jack is publicly supporting the decentralization of social identity and discovery.\n\nThis is the inflection point for DeSo. Why?🧵",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1648929122,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1649603176,
                    "like_count": 179,
                    "diamond_count": 100,
                    "diamond_value": 80950000,
                    "repost_count": 22,
                    "quote_count": 13,
                    "comment_count": 53,
                    "reply_count": 33,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0,
                    "award_count": 0,
                    "award_value": 0
                },
                "hash": "8cf912cbb112a354c048e28d794a78112598ada2d467aac801520f5d121b86bd",
                "account": {
                    "height": 1494,
                    "pubkey": "BC1YLhyuDGeWVgHmh3UQEoKstda525T1LnonYWURBdpgWbFBfRuntP5",
                    "balance": 6774326824,
                    "timestamp": 1614605873,
                    "last_seen": 1649649898,
                    "profile": {
                        "timestamp": 1614605873,
                        "is_hidden": false,
                        "height": 1493,
                        "username": "nader",
                        "description": "Creator of the DeSo blockchain, head of the DeSo Foundation (deso.org), and founder of @daodao.\n\n(D,D)",
                        "avatar_url": "http://media.overdeso.lo/avatar/gPjusuCXegC",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 98236459993,
                        "locked": 948022571856,
                        "watermark": 191168572431,
                        "price": 28951246819
                    },
                    "dao": null,
                    "extra": null
                }
            },
            {
                "depth": 1,
                "is_quoted": false,
                "text": "People are tired of five companies controlling all of the world's information\n\nPeople are tired of black-box feed algorithms that shadow-ban them overnight\n\nPeople are tired of being slaves to ads-driven profit-seeking corporations\n\nAnd DeSo is the answer",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1648929122,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1649632379,
                    "like_count": 60,
                    "diamond_count": 28,
                    "diamond_value": 6250000,
                    "repost_count": 1,
                    "quote_count": 8,
                    "comment_count": 14,
                    "reply_count": 0,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0,
                    "award_count": 0,
                    "award_value": 0
                },
                "hash": "5daf82b57c4fff2fe9fc814c69e8f8b81baaf7be777156bb8fa15e1e5de61bab",
                "account": {
                    "height": 1494,
                    "pubkey": "BC1YLhyuDGeWVgHmh3UQEoKstda525T1LnonYWURBdpgWbFBfRuntP5",
                    "balance": 6774326824,
                    "timestamp": 1614605873,
                    "last_seen": 1649649898,
                    "profile": {
                        "timestamp": 1614605873,
                        "is_hidden": false,
                        "height": 1493,
                        "username": "nader",
                        "description": "Creator of the DeSo blockchain, head of the DeSo Foundation (deso.org), and founder of @daodao.\n\n(D,D)",
                        "avatar_url": "http://media.overdeso.lo/avatar/gPjusuCXegC",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 98236459993,
                        "locked": 948022571856,
                        "watermark": 191168572431,
                        "price": 28951246819
                    },
                    "dao": null,
                    "extra": null
                }
            },
            {
                "depth": 2,
                "is_quoted": false,
                "text": "With DeSo all content is stored on-chain, and all code is 100% open-source, even the feed algorithms.\n\nWhy is this \"open firehose\" important?\n\nBecause now there can be hundreds of apps, not five, and posts on one app can show up in all the others, which wasn't possible before.",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1648929122,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1649574022,
                    "like_count": 27,
                    "diamond_count": 13,
                    "diamond_value": 1000000,
                    "repost_count": 1,
                    "quote_count": 0,
                    "comment_count": 9,
                    "reply_count": 0,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0,
                    "award_count": 0,
                    "award_value": 0
                },
                "hash": "89ac9d138d469a46d12e88c4981851e77c827c48486418ac0272546514575273",
                "account": {
                    "height": 1494,
                    "pubkey": "BC1YLhyuDGeWVgHmh3UQEoKstda525T1LnonYWURBdpgWbFBfRuntP5",
                    "balance": 6774326824,
                    "timestamp": 1614605873,
                    "last_seen": 1649649898,
                    "profile": {
                        "timestamp": 1614605873,
                        "is_hidden": false,
                        "height": 1493,
                        "username": "nader",
                        "description": "Creator of the DeSo blockchain, head of the DeSo Foundation (deso.org), and founder of @daodao.\n\n(D,D)",
                        "avatar_url": "http://media.overdeso.lo/avatar/gPjusuCXegC",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 98236459993,
                        "locked": 948022571856,
                        "watermark": 191168572431,
                        "price": 28951246819
                    },
                    "dao": null,
                    "extra": null
                }
            },
            {
                "depth": 3,
                "is_quoted": false,
                "text": "Don't like one app's curation?\n\nYou have *hundreds* of alternatives, including http://diamondapp.com, http://cloutfeedapp.com, http://supernovas.app, http://desocialworld.com, http://nftz.zone, http://polygram.cc, and more on http://desolist.cc.",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1648929122,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1649094527,
                    "like_count": 18,
                    "diamond_count": 9,
                    "diamond_value": 450000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 7,
                    "reply_count": 0,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0,
                    "award_count": 0,
                    "award_value": 0
                },
                "links": [
                    {
                        "title": "Welcome to Diamond",
                        "description": "Don't settle for a like. Get diamonds and invest in creators like never before.",
                        "image": "https://diamondapp.com/assets/diamond/camelcase_logo_og.jpg",
                        "image:width": "1200",
                        "image:height": "630",
                        "image:type": "image/jpeg",
                        "url": "http://diamondapp.com"
                    },
                    {
                        "image": "http://cloutfeedapp.com/wp-content/uploads/2021/05/iPhone-11-Pro-Free-Premium-Mockup-PSD-2-min.png",
                        "url": "http://cloutfeedapp.com"
                    },
                    {
                        "title": "Supernovas",
                        "description": "The decentralized social network for Web3. Buy and sell DeSo NFT's, invest in Creator Coins, and connect with others through feeds, posts, and direct messages.",
                        "image": "https://supernovas.app/assets/img/regular-meta.png",
                        "image:type": "image/jpeg",
                        "url": "http://supernovas.app"
                    }
                ],
                "hash": "8d3f9ffd9f325869b22e731aacdc1c46850f49fbe30204570394af79e440a963",
                "account": {
                    "height": 1494,
                    "pubkey": "BC1YLhyuDGeWVgHmh3UQEoKstda525T1LnonYWURBdpgWbFBfRuntP5",
                    "balance": 6774326824,
                    "timestamp": 1614605873,
                    "last_seen": 1649649898,
                    "profile": {
                        "timestamp": 1614605873,
                        "is_hidden": false,
                        "height": 1493,
                        "username": "nader",
                        "description": "Creator of the DeSo blockchain, head of the DeSo Foundation (deso.org), and founder of @daodao.\n\n(D,D)",
                        "avatar_url": "http://media.overdeso.lo/avatar/gPjusuCXegC",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 98236459993,
                        "locked": 948022571856,
                        "watermark": 191168572431,
                        "price": 28951246819
                    },
                    "dao": null,
                    "extra": null
                }
            },
            {
                "depth": 4,
                "is_quoted": false,
                "text": "Make just ONE profile on any app, and you now have an identity that is *portable* across all the others. The last profile you'll ever have to make.\n\nPost once, get reach from *everywhere*.\n\nAnd when content is open, apps compete to make you *happy*, not keep you scrolling forever",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1648929122,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1649179196,
                    "like_count": 22,
                    "diamond_count": 10,
                    "diamond_value": 500000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 6,
                    "reply_count": 0,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0,
                    "award_count": 0,
                    "award_value": 0
                },
                "hash": "ae90ff2f644373c1dfc5d3acfa1c07164ab838003def4716e3888837549c1d7a",
                "account": {
                    "height": 1494,
                    "pubkey": "BC1YLhyuDGeWVgHmh3UQEoKstda525T1LnonYWURBdpgWbFBfRuntP5",
                    "balance": 6774326824,
                    "timestamp": 1614605873,
                    "last_seen": 1649649898,
                    "profile": {
                        "timestamp": 1614605873,
                        "is_hidden": false,
                        "height": 1493,
                        "username": "nader",
                        "description": "Creator of the DeSo blockchain, head of the DeSo Foundation (deso.org), and founder of @daodao.\n\n(D,D)",
                        "avatar_url": "http://media.overdeso.lo/avatar/gPjusuCXegC",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 98236459993,
                        "locked": 948022571856,
                        "watermark": 191168572431,
                        "price": 28951246819
                    },
                    "dao": null,
                    "extra": null
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.comment.list

Get list of comments for post hash or for some account.&#x20;

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>lang</td><td></td><td>false</td><td>Languge code to fetch. Default is null so means any language</td></tr><tr><td>depth</td><td></td><td>false</td><td>Max depth to fetch. Default is null</td></tr><tr><td>has_media</td><td></td><td>false</td><td>Fetch posts that have media only</td></tr><tr><td>has_video</td><td></td><td>false</td><td>Fetch posts that have video only</td></tr><tr><td>has_image</td><td></td><td>false</td><td>Fetch posts that have image only attached to it</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of comments in chronological order that represent post structure.

#### Examplees

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.comment.list", "params": {"account": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1   | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "depth": 1,
                "is_quoted": false,
                "text": "Could this be the rarest of them all? @charlie",
                "lang": "en",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1635356303,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1635767361,
                    "like_count": 2,
                    "diamond_count": 1,
                    "diamond_value": 50000,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 2,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "hash": "e3403e1075fb7222d3b122333a47274a67870be896ff623580a05b9a7b7f9c2a",
                "root": {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "BEHOLD MATIES!",
                    "lang": "ku",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1635356303,
                    "hash": "696c39c9023838460fa562c888381328665d3ed9c0da1ab07b8866339328783c",
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 1202813160669,
                        "timestamp": 1615574505,
                        "profile": {
                            "timestamp": 1615574830,
                            "is_hidden": false,
                            "height": 6043,
                            "username": "diamondhands",
                            "description": "💎🙌",
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                            "reward_points": 0,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 164216917444,
                            "locked": 4578658488257,
                            "watermark": 255810788786,
                            "price": 27881771010
                        }
                    }
                },
                "parent": {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "BEHOLD MATIES!",
                    "lang": "ku",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1635356303,
                    "hash": "696c39c9023838460fa562c888381328665d3ed9c0da1ab07b8866339328783c",
                    "account": {
                        "height": 6042,
                        "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                        "balance": 1202813160669,
                        "timestamp": 1615574505,
                        "profile": {
                            "timestamp": 1615574830,
                            "is_hidden": false,
                            "height": 6043,
                            "username": "diamondhands",
                            "description": "💎🙌",
                            "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                            "reward_points": 0,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 164216917444,
                            "locked": 4578658488257,
                            "watermark": 255810788786,
                            "price": 27881771010
                        }
                    }
                },
                "account": {
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "balance": 1202813160669,
                    "timestamp": 1615574505,
                    "profile": {
                        "timestamp": 1615574830,
                        "is_hidden": false,
                        "height": 6043,
                        "username": "diamondhands",
                        "description": "💎🙌",
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                        "reward_points": 0,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 164216917444,
                        "locked": 4578658488257,
                        "watermark": 255810788786,
                        "price": 27881771010
                    }
                },
                "state": {
                    "is_liked": false,
                    "diamond_level": 0
                }
            },
            {
                "depth": 0,
                "is_quoted": true,
                "text": "BEHOLD MATIES!",
                "lang": "ku",
                "has_media": false,
                "has_image": false,
                "has_video": false,
                "media": null,
                "is_hidden": false,
                "is_nft": false,
                "submitted_at": 1635356303,
                "nft": null,
                "stat": {
                    "last_stat_ts": 1641159951,
                    "like_count": 273,
                    "diamond_count": 45,
                    "diamond_value": 111950000,
                    "repost_count": 2,
                    "quote_count": 3,
                    "comment_count": 30,
                    "nft_bid_count": 0,
                    "nft_trade_count": 0,
                    "nft_burned_count": 0
                },
                "hash": "696c39c9023838460fa562c888381328665d3ed9c0da1ab07b8866339328783c",
                "root": null,
                "parent": null,
                "account": {
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "balance": 1202813160669,
                    "timestamp": 1615574505,
                    "profile": {
                        "timestamp": 1615574830,
                        "is_hidden": false,
                        "height": 6043,
                        "username": "diamondhands",
                        "description": "💎🙌",
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                        "reward_points": 0,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 164216917444,
                        "locked": 4578658488257,
                        "watermark": 255810788786,
                        "price": 27881771010
                    }
                },
                "state": {
                    "is_liked": false,
                    "diamond_level": 0
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.share.list

Get shares for requested post.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns list of shares for this posts (including quoted reposts).

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.share.list", "params": {"hash":"ba4c4e15c4f2d88aa54c037e313f0c186ee879bba832f6d47ebf01800ee04b94", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 45,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "Don has been a great friend over here. Cheers to his upcoming project. Do check out @overclout",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1643741929,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1643741929,
                        "like_count": 2,
                        "diamond_count": 3,
                        "diamond_value": 5000000,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "links": null,
                    "hash": "9671da669f5cbbe42ee6eef5c6c6b8b7d99c9780149d2f6a740c2cbad42d3129",
                    "account": {
                        "height": 25636,
                        "pubkey": "BC1YLijYAbrxqpa7Kk89KqqxPRzMCJc6hvWR921uFbATqyEmGqh565b",
                        "balance": 9426123299,
                        "timestamp": 1621371212,
                        "profile": {
                            "timestamp": 1621371212,
                            "is_hidden": false,
                            "height": 25635,
                            "username": "sidz",
                            "description": "【S】【i】【d】【z】\n\nBorn at a very young age\n\n🎀  𝐼 𝒶𝓂  🎀\nA\nPoet,\nLover,\nDreamer,\nDoer,\nPhilosopher,\nHuman.",
                            "avatar_url": "http://media.overdeso.lo/avatar/WXL2bGiNc61",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 23758600862,
                            "locked": 13422468295,
                            "watermark": 27062890289,
                            "price": 1694856071
                        },
                        "dao": null
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "👌",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1643739653,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1643739653,
                        "like_count": 1,
                        "diamond_count": 0,
                        "diamond_value": 0,
                        "repost_count": 0,
                        "quote_count": 0,
                        "comment_count": 0,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "links": null,
                    "hash": "9b5d81a3ad3259c3deb68969d426b65b90ea1bb6d3fd81e2e459974a728e1c44",
                    "account": {
                        "height": 57819,
                        "pubkey": "BC1YLgM8aVyYxKhxHjRZ3gvXD6Etjp2okYpWbTGXdHFFbxCjVQjoMQC",
                        "balance": 300099228,
                        "timestamp": 1630846827,
                        "profile": {
                            "timestamp": 1631020018,
                            "is_hidden": false,
                            "height": 58342,
                            "username": "APEX69",
                            "description": "Deso lover's crypto passion. music and painting love. 8 F.R enjoy it.",
                            "avatar_url": "http://media.overdeso.lo/avatar/RqtBXYUYnCD",
                            "reward_points": 1000,
                            "stake_points": 12500
                        },
                        "coin": {
                            "supply": 18973595109,
                            "locked": 6830448750,
                            "watermark": 19573726297,
                            "price": 1079992915
                        },
                        "dao": null
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.like.list

Get post likes or likes of posts for account.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr></tbody></table>

#### Response

The method returned likes in chronological order for post or for account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.like.list", "params": {"hash":"75f16239b57de0531f9579f3817beb0a67515e4999947f293c112fb0260178e4", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "post": {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "In retrospect, it was inevitable",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": true,
                    "submitted_at": 1615574830
                },
                "account": {
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "balance": 1202557738544,
                    "timestamp": 1615574505,
                    "profile": {
                        "timestamp": 1615574830,
                        "is_hidden": false,
                        "height": 6043,
                        "username": "diamondhands",
                        "description": "💎🙌",
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                        "reward_points": 0,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 164217523869,
                        "locked": 4578709213058,
                        "watermark": 255810788786,
                        "price": 27881976936
                    }
                }
            },
            {
                "post": {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "In retrospect, it was inevitable",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": true,
                    "submitted_at": 1615574830
                },
                "account": {
                    "height": 6042,
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "balance": 1202557738544,
                    "timestamp": 1615574505,
                    "profile": {
                        "timestamp": 1615574830,
                        "is_hidden": false,
                        "height": 6043,
                        "username": "diamondhands",
                        "description": "💎🙌",
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PzJRxZS1",
                        "reward_points": 0,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 164217523869,
                        "locked": 4578709213058,
                        "watermark": 255810788786,
                        "price": 27881976936
                    }
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.diamond.list

Fetch diamond list for post hash or account as receiver or sender.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

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
    curl -s --data '[{"method":"post.diamond.list", "params": {"account": "diamondhands", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
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
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615574830,
                    "text": "In retrospect, it was inevitable"
                },
                "receiver": {
                    "balance": 1568580768648,
                    "coin": {
                        "locked": 5625110063387,
                        "price": 31982730622,
                        "supply": 175879606086,
                        "watermark": 255810788786
                    },
                    "height": 6042,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PxVxfRr8",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6043,
                        "is_hidden": false,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "timestamp": 1615574830,
                        "username": "diamondhands"
                    },
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "timestamp": 1615574505
                },
                "sender": {
                    "balance": 26709020091,
                    "coin": {
                        "locked": 1119643937314,
                        "price": 10784891159,
                        "supply": 103815970024,
                        "watermark": 166627229450
                    },
                    "height": 6055,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/ZsYUGJvrVLC",
                        "description": "Community Builder \ud83d\udc4f on $CLOUT Ecosystem & Clubhouse\n\n// Projects //\n\n@GiftClout\ud83d\udc9d Co-founder\nBuilding/Dreaming up Gift Economy Node of $CLOUT Ecosystem\n\n@FBV\u2705 Founder & Managing Director\nInvestments into Projects aligned with a new paradigm\n\n@BitCloutUniversity\ud83c\udfeb Founder\nPlatform for Education & Empowerment onto the BitClout Platform & Ecosystem\n\n// Topics of Interest //\n\n\ud83d\udc4f Conscious Community\n\ud83c\udf81 Gift Economy\n\ud83d\udd17 Blockchain\n\ud83d\udc65 Relationships\n\ud83d\ude4f\ud83c\udffd Trust\n\ud83e\udd1d Reputation\n\ud83d\udcb8 Wealth Redistribution\n\ud83d\ude4c Philanthropy",
                        "height": 6061,
                        "is_hidden": false,
                        "reward_points": 222,
                        "stake_points": 12500,
                        "timestamp": 1615580501,
                        "username": "RajLahoti"
                    },
                    "pubkey": "BC1YLiRgvtCW3vwhy8jYahJoi5XmbrxSHrZHVPLBJm3cxWDKQ9vvwE8",
                    "timestamp": 1615578129
                }
            },
            {
                "diamond": {
                    "level": 6,
                    "value": 5000000000
                },
                "post": {
                    "depth": 0,
                    "has_image": false,
                    "has_media": false,
                    "has_video": false,
                    "is_hidden": false,
                    "is_nft": true,
                    "is_quoted": false,
                    "lang": "en",
                    "media": {
                        "image_urls": []
                    },
                    "submitted_at": 1615574830,
                    "text": "In retrospect, it was inevitable"
                },
                "receiver": {
                    "balance": 1568580768648,
                    "coin": {
                        "locked": 5625110063387,
                        "price": 31982730622,
                        "supply": 175879606086,
                        "watermark": 255810788786
                    },
                    "height": 6042,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Xs8PxVxfRr8",
                        "description": "\ud83d\udc8e\ud83d\ude4c",
                        "height": 6043,
                        "is_hidden": false,
                        "reward_points": 0,
                        "stake_points": 12500,
                        "timestamp": 1615574830,
                        "username": "diamondhands"
                    },
                    "pubkey": "BC1YLgU67opDhT9bTPsqvue9QmyJLDHRZrSj77cF3P4yYDndmad9Wmx",
                    "timestamp": 1615574505
                },
                "sender": {
                    "balance": 33447301750,
                    "coin": {
                        "locked": 480232732699,
                        "price": 6132459458,
                        "supply": 78309972683,
                        "watermark": 79534264925
                    },
                    "height": 9768,
                    "profile": {
                        "avatar_url": "https://overdeso.com/media/avatar/Rg4v2QyWq1z",
                        "description": "GiftClout.com\ud83d\udc9d :: The Gift Economy Social Network\n\nApply for Verification \u2705 during our open beta. \n\nIncludes:\n\n- Invitation to Private Beta Tester Telegram Group\n\n- Whitelisted in GiftClout\u2019s Global Feed\n\n- Inclusion in Our Supporters section \n\nYou can apply for verification by contributing to the $GiftClout coin when you hold 0.1 or more.",
                        "height": 9775,
                        "is_hidden": false,
                        "reward_points": 2200,
                        "stake_points": 12500,
                        "timestamp": 1616712097,
                        "username": "GiftClout"
                    },
                    "pubkey": "BC1YLhKYCXfy2tguomfrydUAEFcf5ANqkaQELWgTHWVVNPB3UHibxth",
                    "timestamp": 1616709041
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.award.list

Fetch award list for post hash or account as receiver or sender.

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch. It has priority if its passed so we ignore account related fields then.</td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

Returns structure as list each on with keys:

* **award** – contains level only of diamond;
* **post** – related post information;
* **sender** – information about sender account;
* **receiver** – information about receiver account.

If no diamonds found returned empty array list there was no error.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
    curl -s --data '[{"method":"post.award.list", "params": {"account": "donhardman", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "award": {
                    "timestamp": 1649609933,
                    "level": 500000,
                    "value": 500000
                },
                "post": {
                    "depth": 0,
                    "is_quoted": true,
                    "text": "💎 Diamond it once, 🎁 gift it many times",
                    "lang": null,
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1649609731,
                    "hash": "cf7e683807b173d23a91a482059e5c3df4dff480f7faf170ecabf3e5a81760a7"
                },
                "sender": {
                    "height": 75338,
                    "pubkey": "BC1YLhZzLUK3bC59sguWuazQpaT4611cr12VXQig4rgiThRDT4Wiq8R",
                    "balance": 16445332670,
                    "timestamp": 1636120919,
                    "last_seen": 1649648088,
                    "profile": {
                        "timestamp": 1636120919,
                        "is_hidden": false,
                        "height": 75337,
                        "username": "Overclout",
                        "description": "The new social app on DeSo.\n\nBuilt with React and powered by @Overdeso.\n\nJoin the public beta!\n\noverclout.com ❤️ by @muvon | discord.gg/Z5wjwyR78d",
                        "avatar_url": "http://media.overdeso.lo/avatar/XhCY887koKr",
                        "reward_points": 1000,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 45486609265,
                        "locked": 94113332049,
                        "watermark": 46154026266,
                        "price": 6207102022
                    },
                    "dao": null,
                    "extra": {
                        "cover": "https://images.deso.org/df7846acd6cac34f749452164bca6c367b394e92ed6a4771a393d3e5cc89cf2f.webp"
                    }
                },
                "receiver": {
                    "height": 11962,
                    "pubkey": "BC1YLgteRL8SgzZLmPyx6hK1tt6XXtaE3m5qAy9GFhP3eGtXmjqEULB",
                    "balance": 204536682,
                    "timestamp": 1617379448,
                    "last_seen": 1649651436,
                    "profile": {
                        "timestamp": 1617379717,
                        "is_hidden": false,
                        "height": 11964,
                        "username": "donhardman",
                        "description": "Free runner & Dev head\n\n@muvon founder",
                        "avatar_url": "http://media.overdeso.lo/avatar/ftdtuWqA5St",
                        "reward_points": 1021,
                        "stake_points": 12500
                    },
                    "coin": {
                        "supply": 30264888783,
                        "locked": 27721560678,
                        "watermark": 30332040189,
                        "price": 2747893473
                    },
                    "dao": null,
                    "extra": {
                        "last_name": "Don",
                        "birth_date": "1988-10-21",
                        "github": "https://github.com/donhardman",
                        "cover": "https://images.deso.org/b17038620978d8d687a184c44a993a042a060533447874bc846ff3b963f25885.webp"
                    }
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.vote.list

Get vote options for post that represents poll

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format to fetch</td></tr><tr><td>account</td><td></td><td>true</td><td>Account username or public key in base58 format or hex without prefix</td></tr><tr><td>offset</td><td></td><td>false</td><td></td></tr><tr><td>limit</td><td></td><td>false</td><td></td></tr></tbody></table>

#### Response

The method returned voting for poll in chronological order for post or for account.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.vote.list", "params": {"account":"epicfail666", "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        [
            {
                "option_index": 3,
                "timestamp": 1644437510,
                "post": {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "One more poll with 4 options",
                    "lang": "en",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": null,
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1644437510,
                    "poll": [
                        [
                            "option 1",
                            0
                        ],
                        [
                            "option 12",
                            0
                        ],
                        [
                            "option 113",
                            0
                        ],
                        [
                            "option 14",
                            1
                        ]
                    ]
                }
            }
        ]
    ]
]
```
{% endtab %}
{% endtabs %}

### post.stat.list

Get post historical statistics

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>hash</td><td></td><td>true</td><td>Post hash in hex format.</td></tr><tr><td>period</td><td></td><td>false</td><td>Aggregation period. One of: hour, day, month. Default is hour</td></tr><tr><td>start_at</td><td></td><td>false</td><td>Timestamp to start our lookup. Default is 1610948544 that is genesis block timestamp. That means we fetch from first stat record.</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

The method returns statistic related data in chronological order (low to high).

**count** – how many rows total in your request.

**list** – list of stat structures of related entity. The list contains also **ts** key for timestamp.

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.stat.list", "params": {"hash":"1b50b5bf8bf7190d60f938443f825de447b01ee865a96b08e1ae5461ad4b5c24", "period": "hour", "start_at": 1618895843, "limit": 2}}]' https://api.overdeso.com/v1 | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 6180,
            "list": [
                {
                    "ts": 1618887600,
                    "like_count": 0,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0
                },
                {
                    "ts": 1618891200,
                    "like_count": 1,
                    "diamond_count": 0,
                    "diamond_value": 0,
                    "repost_count": 0,
                    "quote_count": 0,
                    "comment_count": 0
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### post.rank.list

Ranked post list

#### Request params

<table><thead><tr><th>Param</th><th data-type="select">Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td>What type of rankings we need to get. Default is <code>diamond_value</code>. Allowed values: <code>diamond_value</code>, <code>like_count</code>,  <code>repost_count</code>,<code>comment_count</code>,<code>reply_count</code>, <code>award_value</code>, <code>engage_count</code></td></tr><tr><td>sorting</td><td></td><td>false</td><td>One of: value or change.<br><code>value</code> – we sort by value for all time.<br><code>change</code> – we sort by daily change on request value rank.</td></tr><tr><td>range</td><td></td><td>false</td><td>Represents list with min max values or default []. First index - min, second one - max. In case you pass it you will get narrowed ranking in this range</td></tr><tr><td>offset</td><td></td><td>false</td><td>Offset to start. Default 0</td></tr><tr><td>limit</td><td></td><td>false</td><td>LImit of list to fetch. Default is 50</td></tr></tbody></table>

#### Response

Returns list of posts ranked by requested type

#### Examples

{% tabs %}
{% tab title="CURL" %}
```shell
curl -s --data '[{"method":"post.rank.list", "params": {"type":"like_count", "offset": 0, "limit": 2}}]' https://api.overdeso.com/v1  | python -m json.tool
```

```json
[
    [
        null,
        {
            "count": 3874120,
            "list": [
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "wwhat happen with u",
                    "lang": "jv",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1620337352,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1626698046,
                        "like_count": 3759,
                        "diamond_count": 6,
                        "diamond_value": 5406860,
                        "repost_count": 1919,
                        "quote_count": 2,
                        "comment_count": 2067,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "rank": {
                        "position": 1,
                        "change": 0
                    }
                },
                {
                    "depth": 0,
                    "is_quoted": false,
                    "text": "Nodes are faster\nThe password is gone\nDo your worst 😈\n\nWhat made things faster? Click for details 👇",
                    "lang": "en",
                    "has_media": false,
                    "has_image": false,
                    "has_video": false,
                    "media": {
                        "image_urls": []
                    },
                    "is_hidden": false,
                    "is_nft": false,
                    "submitted_at": 1617168348,
                    "nft": null,
                    "stat": {
                        "last_stat_ts": 1640646369,
                        "like_count": 2183,
                        "diamond_count": 21,
                        "diamond_value": 11028188,
                        "repost_count": 4,
                        "quote_count": 2,
                        "comment_count": 907,
                        "nft_bid_count": 0,
                        "nft_trade_count": 0,
                        "nft_burned_count": 0
                    },
                    "rank": {
                        "position": 2,
                        "change": 0
                    }
                }
            ]
        }
    ]
]
```
{% endtab %}
{% endtabs %}
