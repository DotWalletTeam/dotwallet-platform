# Miners Merchant API
Merchant API is an additional service that miners can offer to merchants.
Dotwallet openplatform developer can obtain free token.
We currently provide a free trial token:561b756d12572020ea9a104c3441b71790acbbce95a6ddbf7e0630971af9424b
[Join Telegram developer group](https://t.me/mempool_develepor)
* [Get fee quote](#jump1)
* [Submit transaction](#jump2)
* [Query transaction status](#jump3)

## <span id="jump1">todo,查询</span>

**Brief Description:** 
Method[`GET`]
>  https://www.ddpurse.com/openapi/mapi/feeQuote
**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

#### Returns:
please references:`https://github.com/bitcoin-sv-specs/brfc-merchantapi`

## <span id="jump2">Submit transaction</span>

Method[`GET`]
>  https://www.ddpurse.com/openapi/mapi/tx/{hash}

**header params**
| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | 是 | string |token |

#### Returns:
please references:`https://github.com/bitcoin-sv-specs/brfc-merchantapi`


## <span id="jump3">Query transaction status</span>
Method[`POST`]
>  https://www.ddpurse.com/openapi/mapi/tx

**header params**
| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | 是 | string |token |

**body params**
| param         | required | Description                       |
| ------------ | -------- | -------------------------- |
| rawtx       | 是       |    交易的raw hex   |

 #### Returns:
please references:`https://github.com/bitcoin-sv-specs/brfc-merchantapi`