---
description: This page will describe changes that affect structures or any methods of API
---

# 📅 Latest changes

### Upcoming (api2)

* new method [**account.autocomplete**](account.md#account.autocomplete) that will replace old one account.search;
* method **account.search** deprecated;
* \++

### February, 21 2022 (api1)

* fix an issue with [**post.comment.list**](post.md#post.comment.list) method when it was returning posts also for a requested account;
* massive update to mempool logic that makes it much more stable and ready to be pre-release version;
* added `hash` to [**post.like.list**](post.md#post.like.list) response;
* added `hash` to [**post.diamond.list**](post.md#post.diamond.list) response;
* new method [**transaction.status**](transaction.md#transaction.status) for getting connect status for transaction;
* added `is_reposted` to post state;
* new method [**account.ping**](account.md#account.ping) for notification of reader state account status;
* new method [**account.online.list**](account.md#account.online.list) that returns account that online.

### February, 17 2022 (api1)

* new method [**post.highlight.list**](post.md#post.highlight.list);
* new method [**account.highlight.list**](account.md#account.highlight.list);
* add basic error checking on [**transaction.submit**](transaction.md#transaction.submit) method.

### February, 09 2022 (api1)

* onchain polls and votes are indexing now;
* added state for poll vote to [**post structure**](structures.md#post) response;
* update [**Overdeso protocol**](overdeso-protocol.md#basic\_transfer) description according to polls changes;
* fix issues with mentions in notifications;
* new method [**post.vote.list**](post.md#post.vote.list).

### February, 07 2022 (api1)

* changed sorting of comments in [**post.comment.list**](post.md#post.comment.list) method (asc now);
* added `timestamp` and `emoji` to response of method [**post.like.list**](post.md#post.like.list);
* fixed incorrect account attached when we fetch likes for post with method [**post.like.list**](post.md#post.like.list);
* fixed issue with attached account entries for [**post.diamond.list**](post.md#post.diamond.list);
* added `timestamp` to response of method [**post.diamond.list**](post.md#post.diamond.list);
* new method [**post.share.list**](post.md#post.share.list) to get all shares for wanted post;
* new method [**post.hot.list**](post.md#post.hot.list) to fetch hot posts feed;
* ****[**notifications**](account.md#account.notification.list) support DAO transfers and posts/comments with mentions now;
* fix issue with calculation of `nft_mint_value`, `nft_mint_count`, `nft_sell_value` and `nft_sell_count` in [**account stat structure**](structures.md#account-stat);
* fix issue with burning DAO coins that could affect resulting amounts;
* add [**post.story.list**](post.md#post.story.list) endpoint and start parsing story by [**Overdeso**](overdeso-protocol.md#submit\_post) protocol since block height #102040;
* we index emotional likes and post poll logic by [**Overdeso**](overdeso-protocol.md#concept) protocol since block height #102040;
* added `poll` key to post response structure that contains list of options if the post has poll.

### January, 30 2022 (api2)

* fixed issue when we mark posts to have media in case of someone build incorrect transaction with empty url in it;
* added `links` to [**post**](post.md) response that contains up to 3 links preview from opengraph meta tags;
* fixed issue with calculation of additional [**NFT**](nft.md) royalties;
* ****[**post.list**](post.md#post.list) returns only creators posts now (without reposts);
* added method [**transaction.decode**](transaction.md#transaction.decode) to decode raw transaction in hex.

### January, 28 2022 (api2)

* added `timestamp` to [**coin.operation.list**](coin.md#coin.operation.list) method response;
* added [**Tool**](tool.md) **** category of API with link preview fetching from opengraph for requested URL;
* added [**post.follow.list**](post.md#post.follow.list) method to get account following feed.

### January, 26 2022 (api2)

* fix some broken API method after mempool implementation;
* stabilze mempool syncing, still expiremental;
* adapt system to hard fork;
* changed [**message stat**](structures.md#message) counters, now it has 2: `member_count` and `message_count`;
* added `buy_now_price` for [**NFT structure**](structures.md#nft) of post;
* added `additional_creator_royalty` and `additional_coin_royalty` to **** [**Post structure**](structures.md#post-nft) when it represents NFT;
* added `is_buy_now`, `buy_now_price`, `min_bid` to [**Post  structure**](structures.md#post-nft) when it represents NFT;
* added `dao_holder_count` and `dao_holding_count` to [**Account stat**](structures.md#account-stat) structure;
* added `dao` struture response to [**Account**](structures.md#account-dao);
* calculate `price` field of `coin` structure in the way same DeSo does;
* changed `holdings` to `creators` and `daos` in [**account.me**](account.md#account.me) method;
* deprecated methods: **account.holding.list**, **account.holding.get** and **account.trade.list**;
* new page with [**coin related methods**](coin.md) that supports DAOs.

### January, 17 2022 (api1)

* added transaction signature check in [**transaction.submit**](transaction.md#transaction.submit) method;
* experimental version of mempool is live;
* adjusted `level_points` in [**account stat**](structures.md#account-stat) structure to reflect user activity;
* added ranking using `level_points` for [**account.rank.list**](account.md#account.rank.list);
* new method [**account.notification.list**](account.md#account.notification.list) to get account related notifications (now supports follow/like/transfer/diamond);
* added `notifications` fetch param to [**account.me**](account.md#account.me) method to fetch latest new notifications;
* fixed issue with incorrect count when requesting transactions for account with `type_id` using [**transaction.list**](transaction.md#transaction.list) method;
* added `price` to [**coin holding**](structures.md#coin-holding) structure;
* added `is_reader` flag to message structure in [**message.conversation.list**](message.md#message.conversation.list) method;
* added `version` to [**message structure**](structures.md#message) that contains encryption version;
* added possibility to get list of mempool transaction by using [**transaction.list**](transaction.md#transaction.list) method;
* account related request params `pubkey` / `username` replaced with one`account` that is autodetected if its username or pubkey;
* block related request params `height` / `hash` replaced with one `block` that is autodetected if its block hash or height;
* reader state header for viewing account changed to `X-Reader-Account` and can be pubkey or username.

### January, 07 2022 (api2)

* added `fetch` param to [**account.me**](account.md#account.me) method for fetching in one request extra data for reader account;
* add support of `comment_count` for [**post rankings**](post.md#post.rank.list);
* `burned` and `fee` are calculated in separated way now to display in [**account stat structure**](structures.md#account-stat);
* added `transaction` type to global [**chain.stat.get**](chain.md#chain.stat.get);
* `tx_count` ranking is deprecated in [**account.rank.list**](account.md#account.rank.list);
* fixed `tx_count` aggregation in global [**chain statistic**](chain.md#chain.stat.get);
* adjusted coin holding response structures, please check examples on [**account.holding.list**](account.md#account.holding.list) page;
* `usd_rate` is showing current rate in [**chain.state**](chain.md#chain.state) method;
* new `level_points` stat for account that represents aggregated activity (more info soon).

### January, 04 2022 (api2)

* new method [**hashtag.post.list**](hashtag.md#hashtag.post.list) to get posts for requested hashtag;
* added [**account structure**](structures.md#account) to all post list response (like to repost/root/parent).

### January, 03 2022 (api2)

* changed response structure of [**account.rank.list**](account.md#account.rank.list) and [**post.rank.list**](post.md#post.rank.list);
* ****[**account.rank.list**](account.md#account.rank.list) and [**post.rank.list**](post.md#post.rank.list) now can return rankings based on daily changes of value;
* new method [**hashtag.rank.list**](hashtag.md#hashtag.rank.list) to get rankings for hashtag.

### January, 02 2022 (api2)

* better performance of indexing the blockchain and reduced latency of responses;
* mempool indexing is deployed and going to be activated ASAP;
* new method [**transaction.submit**](transaction.md#transaction.submit) to broadcast signed raw transaction hex to the blockchain;
* we started to add [**Overdeso protocol**](overdeso-protocol.md) description in docs step by step;
* new method [**account.search**](account.md#account.search) mainly to lookup accounts by username prefix;
* new [**message.conversation.list**](message.md#message.conversation.list) method to get latest conversations for account;
* updated structure of request/response for method [**message.list**](message.md#message.list);
* new method [**account.holding.get**](account.md#account.holding.get) for fast fetch of information for exact creator coin holding;
* new method [**account.follow.get**](account.md#account.follow.get) for fast fetch of information account follows another one;
* we count transactions for account by its time, you can find counters in **stat** field response;
* new fields in stat of [**account structure**](structures.md#account-stat) response;
* updated method [**account.list**](account.md#account.list) with different request params;
* new method [**account.rank.list**](account.md#account.rank.list) to fetch all time rankings for accounts;
* method [**chain.stat.get**](chain.md#chain.stat.get) works now;
* we collect total `fee`, `burned` and `transactor_tx_count` stats for each [**account**](account.md#account.get) now;
* method [**hashtag.list**](hashtag.md#hashtag.list) returns most hashtags in most recent usage order;
* new method [**account.me**](account.md#account.me) to get current reader account related info (now works same as account.get but will be extended for reader state data);
* extracted [**post.comment.list**](post.md#post.comment.list) method to fetch comments for related post or for account;
* updated method [**post.list**](post.md#post.list) now returns global recent posts if no params passed;
* new method [**post.rank.list**](post.md#post.rank.list) for fetching ranked post list.

### December, 20 2021 (api1)

* added statistic for [**posts**](post.md#post.stat.list)/[**hashtags**](hashtag.md#hashtag.stat.list)/[**accounts**](account.md#account.stat.list) for daily/monthly periods;
* fixed data issue with hour period for statistics;
* new method [**chain.stat.get**](chain.md#chain.stat.get) for current chain stat (not aggregated yet, data is coming on next update);
* ****[**nft.bid.list**](nft.md#nft.bid.list) now accepts sorting;
* new method [**account.list**](account.md#account.list) to fetch accounts sorted by locked, balance or profile creation time;
* added possibility to filter [**account transactions**](transaction.md#transaction.list) by type;
* added possibility to get [**list of block transactions**](transaction.md#transaction.list) and filter them by type;
* calculate count in proper way for posts/hashtags/accounts stat list methods;
* fix issue with incorrect offset behavior in list endpoints;
* min limit is set to `1` instead of `5`, error returned in case you pass wrong offset/limit in list endpoints;
* improved stability of blockchain syncing;
* added `timestamp` field to account response (profile and account), showing timestamp of creation account/profile;
* ****[**account structure**](structures.md#account) response is modified, take a look this breaking change;
* new param `expand` in [**account.follow.list**](account.md#account.follow.list) method to return expanded account info;
* you can pass `X-Account-Pubkey` or `X-Account-Username` in header for fetching reader state;
* new `state` field in [**account.follow.list**](account.md#account.follow.list), [**account.get**](account.md#account.get), [**post.get**](post.md#post.get), [**post.list**](post.md#post.list) that reflects reader state;
* updated [**structures**](structures.md) docs;
* new method [**message.list**](message.md#message.list) to fetch latest messages for account as recipient or sender;
* added filter flags `has_image`, `has_video`, `has_media` to [**post.list**](post.md#post.list) method;
* added [**account.upload.url**](account.md#account.upload.url) to get upload url for media content;
* `last_ts` filtering for [**hashtag.list**](hashtag.md#hashtag.list).

### December, 13 2021 (api2)

* added [**NFT**](nft.md) related methods;
* new method [**block.list**](block.md#block.list) to fetch latest list of mined blocks.

### December, 11 2021 (api2)

* added **balance** and **utxo\_count** fields to [account](account.md) stat structure;
* added **info** field to [block](block.md) structure that contains various statistic for block (same as for transaction);
* **diamond.list** moved to [post](post.md) namespace [**post.diamond.list**](post.md#post.diamond.list);
* new method [**account.utxo.list**](account.md#account.utxo.list) to fetch spendable transactions and whole spendable balance for an account;
* new method [**account.trade.list**](account.md#account.trade.list) to fetch creator coin trading and transfers;
* new page with response [**structures**](structures.md) information, work in progress for now;
* new methods to fetch various information about [**hashtags**](hashtag.md);
* new method [**account.stat.list**](account.md#account.stat.list) to fetch historical statistics for account. ⚠️Only for hour period now;
* new method [**post.stat.list**](post.md#post.stat.list) to fetch historical statistic for post. ⚠️Only for hour period now;
* new method [**hashtag.stat.list**](hashtag.md#hashtag.stat.list) to fetch historical statistic for hashtags usage. ⚠️Only for hour period now;
* new method [**chain.state**](chain.md#chain.state) to fetch current blockchain state info;
* all data are in sync with new blocks now (but not mempool yet).

### December, 7 2021 (api1)

Initial version of early beta access is here. And we will describe all breaking changes in API since now. 🚀
