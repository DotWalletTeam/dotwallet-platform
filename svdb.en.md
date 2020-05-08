# svdb
Developers can query some information of BSV chain,currently, we provide a free interface, which can query 10,000 times a day.
* [Query merkle-tree](#jump1)
* [Query blockheader](#jump2)
* [Query transaction ](#jump3)
* [Get address info](#jump4)
* [Query address's UTXO](#jump5)
* [Query address's inventory](#jump6)
* [Query Block info by block hash ](#jump7)
* [Query block info by height](#jump8)
* [Query batch blocks info by height](#jump9)
* [Get transactions of block](#jump10)
* [Get chain info](#jump11)
* [Query remaining times](#jump12)
* [Get free token](#jump13)

## <span id="jump1">merkle-tree query</span>

**Brief description：** 
- query merkle path by txid

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/merkle`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| txid | YES | string | transaction hash |

 **Returns**

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
 **Return param description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json | return data |
| txs| int | transaction count of block |
| flags| string | The flag described by bip37 is used to calculate the mekle root with the hash array|
| blockhash| string | block hash |
| hashes| [string] | merkle path hash |

## <span id="jump2">BlockHeader query</span>

**Brief description：** 
- Get raw block header by block hash

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/raw/hash/blockheader`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| blockhash | YES | string | block hash |

 **Returns**

```json 
{
	"code": 0,
	"msg": "",
	"data": "02000000028f2cb75e0b6b2bcaba83efa34cb6af4a7bc04e882de8c2090000000000000023d7fee87f54bfb980f383b80742ac060bb5294ff9cb82d159caa8acaf1eec1647f9fc51f2db721961769100"
}
```
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| string | hex string of block header |

## <span id="jump3">Transaction query</span>
**Brief description：** 
- Get transaction detail by txid

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/transaction`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| txid | YES | string | transaction hash |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| vouts| json |  |
| vins| json |  |
| index| int |   |
| confirmation| int |    |
| timestamp| int |    |
| size| int |    |
| value| int |   |
| script| string |  hex string script |
| txid| string |  transaction hash |
| height| int |    |

## <span id="jump4">Get address info</span>
**Brief description：** 
- Get balance and trasaction count of address.

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/address/info`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| address | YES | string |  |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json | |
| transactions| int |  |
| balance| int | |



## <span id="jump5">Query address's UTXO</span>
**Brief description：** 
- Query address's UTXO ,only support p2pkh address temporarily

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/address/utxo`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| address | YES | string |  |
| offset | YES | int |  |
| limit | YES | int | max:100 |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| txid| string |  |
| index| int | |
| height| int | |
| value| int | amount |
| sigscript|string | utxo locking script|



## <span id="jump6">Query address's inventory</span>
**Brief description：** 
- Get address inventory, only support p2pkh address.

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/address/inventory`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| address | YES | string |  |
| offset | YES | int |  |
| limit | YES | int | max:100 |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| txid| string | transaction hash |
| height| int |  |
| value| int | amount |
| sigscript|string | hex string script |



## <span id="jump7">Query Block info by block hash</span>
**Brief description：** 
- 根据block hash查询区块信息

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/block/hash`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| hash | YES | string | block hash |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| height| int |  |
| hash| string | block hash |
| size| int |  |
| timestamp| int |  |
| reward| int |  |
| hex_coinbase| string |  hex string of script|
| transaction_count| int |  |



## <span id="jump8">Query block info by height</span>
**Brief description：** 
- Query block info by height

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/block/height`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| height | YES | int |  |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| height| int |  |
| hash| string | block hash |
| size| int |  |
| timestamp| int |  |
| reward| int |  |
| hex_coinbase| string |  hex string of script|
| transaction_count| int |  |




## <span id="jump9">Query batch blocks info by height</span>
**Brief description：** 
- Query batch blocks info by height order by height desc.

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/blocks/height`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| offset | YES | int |  |
| limit | YES | int | max:100 |

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| height| int |  |
| hash| string | block hash |
| size| int |  |
| timestamp| int |  |
| reward| int |  |
| hex_coinbase| string | |
| transaction_count| int |  |



## <span id="jump10">Get transactions of block</span>
**Brief description：** 
- Get transactions of block

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/block/transaction`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**params：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| hash | YES | string | block hash |
| offset | YES | int |  |
| limit | YES | int |  |

 **Returns**

```json 
{
	"code": 0,
	"msg": "",
	"data": ["4ef83acd026495adff7dfb276bfaf271b0e6ba6c2bc462ef105dd8e1c5fc29f4", "9de197b307f650835765150bff25220408eb6d2d753990645d38bd085ff72053", "1d6982b15f828b77f48146cee3f4f8a4658c0a9dce287e59b27dc14ee9654780", "51679f5421403d13b204827f5e09f0c1316a311645f850ec925007d6ae135fe4", "81a95fab656ca6fe6060d9d202419e00a34c400d3c8215b33ec06e5f10a4b033"]
}
```
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data|  |  |



## <span id="jump11">Get chain info</span>
**Brief description：** 
- Get chain info

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/BSV/chain/info`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

 **Returns**

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
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| json |  |
| bestblock| int | best block height |
| unconfirm_tx_count| int | |
| bestfeerate| json | |
| feebyte| int |  |
| feesatoshi| int |  |
| hashes_per_sec| float |  |
| diffculty| float |  |



## <span id="jump12">Query remaining times</span>
**Brief description：** 
- Query remaining times

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/token/count`

**header params**

| param | required | Type |Description|
| ------ | ------ | ------ |------|
| token | YES | string |token |

**Method：**

- GET

**Returns**

```json 
{
	"code": 0,
	"msg": "",
	"data":1000
}
```
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| int | left count |



## <span id="jump13">get free token</span>
**Brief description：** 
- Get free token
**Method：**

- GET

**header参数：** 

|param|required|Type|Description|
|:----    |:---|:----- |-----   |
| appid | YES | string | merchant'sappid |
| appsecret | YES | string | appsecret |

**Request URL：** 
- ` https://www.ddpurse.com/openapi/svdb/token`

 **Returns**

```json 
{
	"code": 0,
	"msg": "",
	"data":"xxxxxxxxxxxxxxxxxxxxx"
}
```
 **Return param Description** 
|param|Type|Description||
|:-----  |:-----|----- |----|
| code| int | 0:success other:failed |
| msg| string |  error message |
| data| string | token |
