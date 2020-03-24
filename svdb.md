# svdb
开发者可以通过打点平台授权机制查询一些相关的链上信息，目前提供免费接口，每日可以查询一万次
* [merkle-tree查询](#jump1)
* [区块头部查询](#jump2)
* [交易查询](#jump3)
* [地址信息查询](#jump4)
* [地址utxo查询](#jump5)
* [地址流水查询](#jump6)
* [根据hash查询区块信息](#jump7)
* [根据高度查询区块信息](#jump8)
* [根据高度批量查看区块信息](#jump9)
* [获取区块交易列表](#jump10)
* [获取区块链上的一些信息](#jump11)
* [获取免费Grandetid](#jump12)
## <span id="jump1">merkle-tree查询</span>

**简要描述：** 
- 通过txid查询交易的merkle路径

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/merkle`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| txid | 是 | string | 交易的id |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": {
		"txs": 156,
		"hashes": ["7ae2ab185a6e501753f6e29e5b6a98ba040098acb7c11ffed9430f22ed5263a3", "cf2a9a7d357a90dc1aad8740f45c60f5f6b878c198153be197a76486382546d2", "95843caf747674b117111bd850ffdf8ae2b0297618d7cd5227c65ff11978c15e", "c96833b5711cdcd1c615b1b037618bbd8f9cea57d147768e94b2e32a190dba6b", "637f452dbceaca1f184ebc385ac675d40e0fc2cca1d5cafa9a908ce3b62e9290", "5a0bc3772c7510405781b4856085eb9f2f3ccfa5a7c67830f7b6d64d15a056b1", "b1918268ba355b551fee2e55292f48292a2b7ff8bbc951a7acb6db97d8223765", "e4eaecd1de4594749a816042d7d80d66c64d5b801f0830e726874aab8345233a", "e64e32e120aced23171e71f99b56bcea3d24e5d18a475792fbe3d41cebb31c76"],
		"flags": "ff0200",
		"blockhash":"000000000000003887df1f29024b06fc2200b55f8af8f35453d7be294df2d214"
	}
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 交易数据 |
| txs| int | 该交易所在的区块的交易数量 |
| flags| string | 经过16进制编码的bip37描述的flag，用来配合hash数组计算mekle root |
| blockhash| string | 区块hash |
| hashes| string数组 | merkle路径上的hash值 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述

## <span id="jump2">区块头部查询</span>

**简要描述：** 
- 通过区块hash获取raw block header

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/raw/hash/blockheader`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| blockhash | 是 | string | 区块hash |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": "02000000028f2cb75e0b6b2bcaba83efa34cb6af4a7bc04e882de8c2090000000000000023d7fee87f54bfb980f383b80742ac060bb5294ff9cb82d159caa8acaf1eec1647f9fc51f2db721961769100"
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| string | 16进制区块头 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump3">交易查询</span>
**简要描述：** 
- 通过txid查询交易

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/transaction`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| txid | 是 | string | 交易hash |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": {
		"txid": "016a195a865e57a24d2f606aef89d8775ed2f8ae9016419542b9ad798574f6f6",
		"vins": [{
			"index": 0,
			"script": "4730440220493447148876bb55b63712c93004384ad0e0b35500ce96949751682afe8e7d4d022050ff787468c73a3ca51207a93805e96de032a2fa2a6fd8a0153c5d99daf92ae6412103396952494b704fd57dbadfb22951c83f700f6dba06d6bcc32da608d4807067e8",
			"value": 1110213
		}, {
			"index": 1,
			"script": "4730440220449daee99fd72d026864fa084ec5a338be4e3c355ff3a7f6d01951c25957b6b702200fe26fb621da1c2df8d870a5bf6029bb6fb775a58c320f5589e90fb7039bbdf5412102e44bf284602e8d6b3cd2492c783a03ee44cd6965c3f91c07f6c2bbe9d8c6ff46",
			"value": 3602800
		}, {
			"index": 2,
			"script": "483045022100c3d55580d62ac027676e5d352be4cc710051726c68d5ff76085682dd4b3636fb02203b5ff2f5b298a42efbabde5273efda8329547de469f32279cae25d5b3984edfd41210286f4ff4da872b42529007bbbfe6bef8368b601874f6e34610028d7e54614c0a4",
			"value": 1424703
		}, {
			"index": 3,
			"script": "473044022047ae5c1c2ac3211418708141633fe6952f8dd8e7d9baa878d2323323f25c3c38022076af30794eabb63dc9d840152c1b29921adeb67c93e8eb39efaa246367524492412102b25439ce52f3b0114575afc12dccffa0583f911a5d99a569d1c3aacb808f0c1c",
			"value": 254000
		}, {
			"index": 4,
			"script": "483045022100d9522a1e107375b184459091855c36c0a2fff577d9270ca140c4f6a253986a1e02200cd4934de777f188fe5d85fc8bbe111569c58b48cb46c0b3cfdc7efad8ce802841210248b88693adf60fbce82045a6885ceba6840d0977f1a64c3504a76a63b024574c",
			"value": 144110712
		}],
		"vouts": [{
			"index": 0,
			"script": "76a9142fa431e514155b7d36955a7b204aca593043128288ac",
			"value": 149500000
		}, {
			"index": 1,
			"script": "76a914cb13d2b179851b7b37a34763a698fabfe401c7bf88ac",
			"value": 1001610
		}],
		"height": 625876,
		"size": 815,
		"timestamp": 1583995981,
		"confirmation": 6
	}
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| vouts| json | 所有的vout |
| vins| json | 所有的vin |
| index| int |  vin 或者 vout 的 index  |
| confirmation| int |  确认数  |
| timestamp| int |  时间戳  |
| size| int |  交易大小  |
| value| int |  数值  |
| script| string |  16进制编码过的脚本  |
| txid| string |  交易的txid  |
| height| int |  区块高度,-1表示未确认  |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述



## <span id="jump4">地址信息查询</span>
**简要描述：** 
- 通过地址查询地址的交易数量以及余额，只支持p2pkh的地址

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/address/info`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| address | 是 | string | 地址 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": {
		"transactions": 161,
		"balance": 10000000000
	}
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| transactions| int | 该地址参与的交易数量 |
| balance| int | 该地址的余额 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump5">地址utxo查询</span>
**简要描述：** 
- 通过地址查询地址utxo，只支持p2pkh的地址

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/address/utxo`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| address | 是 | string | 地址 |
| offset | 是 | int | 偏移 |
| limit | 是 | int | 条目，最大为100 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": [{
		"value": 10000000000,
		"txid": "35f81304c4966b3be6ee750069071005810c2006adf962bbca368840f7561581",
		"index": 3,
		"height": 625881,
		"sigscript": "dqkUEqpEM1Ja8xNPxBD/Uu7TcZLllEeIrA=="
	}]
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| txid| string | 交易id |
| index| int | utxo是该交易的第几个output |
| height| int | 该交易的高度 |
| value| int | 金额 |
| sigscript|string | utxo锁定脚本 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述



## <span id="jump6">地址流水查询</span>
**简要描述：** 
- 通过地址查询地址流水，只支持p2pkh的地址

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/address/inventory`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| address | 是 | string | 地址 |
| offset | 是 | int | 偏移 |
| limit | 是 | int | 条目，最大为100 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": [{
		"txid": "b064989072bab185984b0106b7f7d3588083f2e2e148a5eb4000f554c9508f66",
		"value": -10000000000,
		"height": -1
	}, {
		"txid": "35f81304c4966b3be6ee750069071005810c2006adf962bbca368840f7561581",
		"value": 10000000000,
		"height": 625881
	}, {
		"txid": "24c4c256cc609596af588fd68100c2ca97f5b8fdea7bbce8f510e9ce4ee6d9ee",
		"value": -10000000000,
		"height": 625852
	}]
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| txid| string | 交易id |
| height| int | 该交易的高度,-1表示为确认 |
| value| int | 金额 |
| sigscript|string | 16进制编码的脚本 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述



## <span id="jump7">根据hash查询区块信息</span>
**简要描述：** 
- 根据区块hash查询区块信息

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/block/hash`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| hash | 是 | string | 区块hash |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": {
		"height": 625882,
		"reward": 1250601893,
		"timestamp": 1583999952,
		"transaction_count": 1771,
		"size": 1015875,
		"hex_coinbase": "03da8c092f68747470733a2f2f636f696e6765656b2e636f6d2f6d696e65722d6f757472656163682f2f4b37633144d892a7db975fcb22337800c0",
		"hash": "0000000000000000017d4326a7232eaefde92465ae77d762c6d1892914e5f0e5"
	}
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| height| int | 高度 |
| hash| string | 区块hash |
| size| int | 大小 |
| timestamp| int | 时间戳 |
| reward| int | 出块奖励 |
| hex_coinbase| string | 16进制编码脚本 |
| transaction_count| int | 交易数量 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump8">根据高度查询区块信息</span>
**简要描述：** 
- 根据高度查询区块信息

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/block/height`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| height | 是 | int | 区块高度 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": {
		"height": 625882,
		"reward": 1250601893,
		"timestamp": 1583999952,
		"transaction_count": 1771,
		"size": 1015875,
		"hex_coinbase": "03da8c092f68747470733a2f2f636f696e6765656b2e636f6d2f6d696e65722d6f757472656163682f2f4b37633144d892a7db975fcb22337800c0",
		"hash": "0000000000000000017d4326a7232eaefde92465ae77d762c6d1892914e5f0e5"
	}
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| height| int | 高度 |
| hash| string | 区块hash |
| size| int | 大小 |
| timestamp| int | 时间戳 |
| reward| int | 出块奖励 |
| hex_coinbase| string | 16进制编码脚本 |
| transaction_count| int | 交易数量 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump9">根据高度批量查看区块信息</span>
**简要描述：** 
- 以高度倒序，批量获取区块

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/blocks/height`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| offset | 是 | int | 偏移 |
| limit | 是 | int | 条目，不超过100 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": [{
		"height": 625890,
		"reward": 1250171398,
		"timestamp": 1584005058,
		"transaction_count": 782,
		"size": 284711,
		"hex_coinbase": "03e28c0904b8ff695e322f537069646572506f6f6c2ffabe6d6dda153ebb0e68d606ba543955fc4aece1fa6ebf31c8dec55114914bb4cfc20a2401000000000000000100076acb69000000000000",
		"hash": "00000000000000000080a268f9d00b7e05a3362884cd525fa540308205af8e04"
	}, {
		"height": 625889,
		"reward": 1250319195,
		"timestamp": 1584004809,
		"transaction_count": 802,
		"size": 368455,
		"hex_coinbase": "03e18c0904c9fe695e088100079a7606000057617270486173685c30",
		"hash": "00000000000000000226910abdfddb05cea178e3eb7f9086b8600a9970fecd9c"
	}]
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| height| int | 高度 |
| hash| string | 区块hash |
| size| int | 大小 |
| timestamp| int | 时间戳 |
| reward| int | 出块奖励 |
| hex_coinbase| string | 16进制编码脚本 |
| transaction_count| int | 交易数量 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述



## <span id="jump10">获取区块交易列表</span>
**简要描述：** 
- 通过地址查询地址utxo，只支持p2pkh的地址

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/block/hash`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| hash | 是 | string | 区块hash |
| offset | 是 | int | 偏移 |
| limit | 是 | int | 条目 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": ["4ef83acd026495adff7dfb276bfaf271b0e6ba6c2bc462ef105dd8e1c5fc29f4", "9de197b307f650835765150bff25220408eb6d2d753990645d38bd085ff72053", "1d6982b15f828b77f48146cee3f4f8a4658c0a9dce287e59b27dc14ee9654780", "51679f5421403d13b204827f5e09f0c1316a311645f850ec925007d6ae135fe4", "81a95fab656ca6fe6060d9d202419e00a34c400d3c8215b33ec06e5f10a4b033"]
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| string字符串数组 | 查询的数据结果 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump11">获取区块链上的一些信息</span>
**简要描述：** 
- 查询区块链的一些信息

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/BSV/block/hash`

**header 头传递参数**

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| Grandetid | 是 | string |token |

**请求方式：**

- POST

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| hash | 是 | string | 区块hash |
| offset | 是 | int | 偏移 |
| limit | 是 | int | 条目 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": {
		"bestblock": 625891,
		"unconfirm_tx_count": 37525,
		"bestfeerate": {
			"feebyte": 1,
			"feesatoshi": 1
		},
		"hashes_per_sec": 2829162.275754181,
		"diffculty": 415922505851.8293
	}
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 查询的数据结果 |
| bestblock| int | 最新高度 |
| unconfirm_tx_count| int | 未确认交易数量 |
| bestfeerate| json | btc表示当前内存池内约0.8m的交易费率，bsv固定返回1:1 |
| feebyte| int | 与feesatoshi配合，表示几字节几聪中的几字节 |
| feesatoshi| int | 与feebyte配合，表示几字节几聪中的几聪 |
| hashes_per_sec| float | 算力 |
| diffculty| float | 难度 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump12">获取免费Grandetid</span>
**简要描述：** 
- 查询区块链的一些信息

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/token/free`

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data":"xxxxxxxxxxxxxxxxxxxxx"
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| string | token |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述


## <span id="jump13">查询剩余次数</span>
**简要描述：** 
- 查询区块链的一些信息

**请求URL：** 
- ` http://blockexplorerapis.mempool.com:4001/v1/data/token/count`

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data":1000
}
```
 **返回参数说明** 
|参数名|类型|说明||
|:-----  |:-----|----- |----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| int | 剩余次数 |
&emsp;
|错误码|说明|
|:-----  |:----     |

- 更多返回错误代码请看首页的错误代码描述