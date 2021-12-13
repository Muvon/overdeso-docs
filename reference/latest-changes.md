---
description: This page will describe changes that affect structures or any methods of API
---

# Latest changes

### December, 13 2021 (api2, upcoming NON breaking changes)

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
