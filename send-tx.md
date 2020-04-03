# 矿工的 Merchant API
开发者通过使用该服务，可以实现查询mempool矿池矿工费率，将交易直接发送至mempool矿池进行广播，查询交易状态。
现阶段提供一个免费的测试token:561b756d12572020ea9a104c3441b71790acbbce95a6ddbf7e0630971af9424b
开发者可以通过打点平台授权机制获取token。
* [查询Mempool矿池矿工费率](#jump1)
* [发送交易Rawtx](#jump2)
* [查询交易状态](#jump3)

## <span id="jump1">查询Mempool矿池矿工费率</span>

**Brief Description:** 
Method[`GET`]
>  https://www.ddpurse.com/openapi/mapi/feeQuote
**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

#### Returns:
please references:`https://github.com/bitcoin-sv-specs/brfc-merchantapi`

## <span id="jump2">发送交易Rawtx</span>

Method[`GET`]
>  https://www.ddpurse.com/openapi/mapi/tx

**header params**
| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | 是 | string |token |

#### Returns:
please references:`https://github.com/bitcoin-sv-specs/brfc-merchantapi`


## <span id="jump3">查询交易状态</span>
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