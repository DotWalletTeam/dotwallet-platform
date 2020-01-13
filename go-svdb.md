# go-svdb

开发者可以通过打点平台授权机制查询一些相关的链上信息，目前提供免费接口，每日可以查询一万次
* [交易查询](#jump1)
* [地址余额查询](#jump2)
* [地址流水查询](#jump3)
* [地址utxo查询](#jump4)
* [剩余次数查询](#jump5)
## <span id="jump1">交易查询</span>

**简要描述：** 
- 通过txid查询交易，目前暂时不支持非p2pkh地址的解析

**请求URL：** 
- `https://www.ddpurse.com/openapi/svdb/transaction`

header 头传递参数

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| appid | 是 | string |appid |
| secret | 是 | string |secret |

**请求方式：**

- GET


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
		"txid": "eae9f30e39e8ac459c3e7af2ef1d78a7d0d79fc9497131dc586ffba099183039",
		"vins": [{
			"index": 0,
			"addr": "1Ex5TjFnU3dGeQX6Hfc1h6c3pbzw8y9AFf"
		}, {
			"index": 1,
			"addr": "1Ex5TjFnU3dGeQX6Hfc1h6c3pbzw8y9AFf"
		}, {
			"index": 2,
			"addr": "1Ex5TjFnU3dGeQX6Hfc1h6c3pbzw8y9AFf"
		}, {
			"index": 3,
			"addr": "1Ex5TjFnU3dGeQX6Hfc1h6c3pbzw8y9AFf"
		}, {
			"index": 4,
			"addr": "17FtWLrNuzoFbhnCZEBo4HQVxYjVBiH3qE"
		}],
		"vouts": [{
			"index": 0,
			"addr": "1NE7ykTddptPrZW1Eg9wGCv4JuvKTnT4da",
			"value": 74449
		}, {
			"index": 1,
			"addr": "17FtWLrNuzoFbhnCZEBo4HQVxYjVBiH3qE",
			"value": 81830
		}, {
			"index": 2,
			"addr": ""
		}],
		"height": 612439
	}
}
```
 **返回参数说明** 
 
|参数名|类型|说明|
|:-----  |:-----|----- |
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 交易数据 |
| txid| string | 交易的txid |
| height| int | 交易的高度，未确认确认的情况为-1 |
| vins| json | 交易的输入 |
| vouts| json | 交易的输出 |
| index| int | 输入或者输出的序号 |
| addr| string | 地址 |
| value| int | 金额，单位为聪 |



&emsp;
## <span id="jump2">地址余额查询</span>
**简要描述：** 
- 查询地址余额，目前暂时不支持非p2pkh地址的解析

**请求URL：** 
- `https://www.ddpurse.com/openapi/svdb/addressBalance`

header 头传递参数

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| appid | 是 | string |appid |
| secret | 是 | string |secret |

**请求方式：**

- GET

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| address | 是 | string | 地址,目前只支持p2pk |

 **返回示例**

``` 
{
	"code": 0,
	"msg": "",
	"data": 75062
}

```
 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|----- |
| code| int | 状态码  0 为成功，其他为失败 |
| msg| string |   错误提示 |
| data| int |   地址余额，返回的数据 |


&emsp;
## <span id="jump3">地址流水查询</span>
**简要描述：** 
- 查询地址流水，目前暂时不支持非p2pkh地址的解析

**请求URL：** 
- `https://www.ddpurse.com/openapi/svdb/addressTxlist`

header 头传递参数

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| appid | 是 | string |appid |
| secret | 是 | string |secret |

**请求方式：**

- GET

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| address | 是 | string | 地址,目前只支持p2pk |
| offset | 是 | int | 偏移，用以分页 |
| limit | 是 | int | 数量，用以分页 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": [{
		"txid": "f904a2ae85e2de9c3e233154082b1aa45100cf281ce08c48516378837d02648a",
		"value": -729707,
		"height": 612868
	}, {
		"txid": "87349d01a4f3a16088ebe3a2aa5c5f168c34380759128dbfaf3a064293ba42c9",
		"value": -224,
		"height": 612442
	}, {
		"txid": "bf4e9d5ba36f7613599111cb66d3c95a0e9f8bd8fb2a82ef7fd223847f7aede1",
		"value": -224,
		"height": 612442
	}, {
		"txid": "f516cc4b34e231d61af811aa2e701a6792566f9048e836f40ecf34f10abab292",
		"value": -224,
		"height": 612442
	}, {
		"txid": "c819198fcf7e9f8aaa2a79cd6cedc61cdbf243768a5f90e635ddfd51bed243f0",
		"value": -224,
		"height": 612442
	}, {
		"txid": "88b9f146429a6888f4bec7669c125f17094e7a5ea31aa4ff51456de5e2ae9972",
		"value": -224,
		"height": 612442
	}, {
		"txid": "928b6d8000c30cb2b8fd66a910e27761cbc475725d5aac83d84e41976987cba9",
		"value": -224,
		"height": 612442
	}, {
		"txid": "08aefe0a2e797a14388e915a6d6ecea25be2bc0c1290d9acc9520c476493cd27",
		"value": -224,
		"height": 612442
	}, {
		"txid": "018b0848ebd30faf8906b6abbfaff9e690e3694b925865ffe2d5691fa834e295",
		"value": -224,
		"height": 612442
	}, {
		"txid": "200dcea0833166f51cf4bf6c904870d5c846c35ed46913d6c5d68d60119c0e7d",
		"value": -224,
		"height": 612442
	}]
}

```
 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|----- |
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | 流水数据 |
| txid| string | 交易的txid |
| height| int | 交易的高度，未确认确认的情况为-1 |
| value| int | 金额，单位为聪 |




&emsp;
## <span id="jump4">地址utxo查询</span>
**简要描述：** 
- 查询地址utxo，目前暂时不支持非p2pkh地址的解析

**请求URL：** 
- `https://www.ddpurse.com/openapi/svdb/addressUtx`

header 头传递参数

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| appid | 是 | string |appid |
| secret | 是 | string |secret |

**请求方式：**

- GET

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| address | 是 | string | 地址,目前只支持p2pk |
| offset | 是 | int | 偏移，用以分页 |
| limit | 是 | int | 数量，用以分页 |

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": [{
		"value": 74449,
		"txid": "eae9f30e39e8ac459c3e7af2ef1d78a7d0d79fc9497131dc586ffba099183039",
		"index": 0,
		"height": 612439,
		"sigscript": "dqkU6NXf0AJXXbECj0+ojJOUpxn9YJaIrA=="
	}, {
		"value": 613,
		"txid": "88b9f146429a6888f4bec7669c125f17094e7a5ea31aa4ff51456de5e2ae9972",
		"index": 0,
		"height": 612442,
		"sigscript": "dqkU6NXf0AJXXbECj0+ojJOUpxn9YJaIrA=="
	}]
}

```
 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|----- |
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| json | utxo数据 |
| txid| string | 交易的txid |
| height| int | 交易的高度，未确认确认的情况为-1 |
| value| int | 金额，单位为聪 |
| index| int | 该utxo为第几个output |
| sigscript| string | pkScript |



&emsp;
## <span id="jump5">剩余次数查询</span>
**简要描述：** 
- 查询每日剩余查询次数

**请求URL：** 
- `https://www.ddpurse.com/openapi/svdb/dayLeftCount`

header 头传递参数

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|
| appid | 是 | string |appid |
| secret | 是 | string |secret |

**请求方式：**

- GET

**参数：** 

| 参数名 | 必选 | 类型 |说明|
| ------ | ------ | ------ |------|

 **返回示例**

```json 
{
	"code": 0,
	"msg": "",
	"data": 9998
}
}
```
 **返回参数说明** 

|参数名|类型|说明|
|:-----|:-----|-----|
| code| int | 状态码，0 为成功，其他为失败 |
| msg| string |  错误提示 |
| data| int | 剩余查询次数 |

