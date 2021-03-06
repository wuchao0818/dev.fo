---
title: 
type: contract
language: zh-cn
order: 1
---
# System Contract

## newaccount

创建合约账户

### 参数

| name        | type   | description                 |
| ----------- | ------ | --------------------------- |
| **creator** | string | 创建者的账户名              |
| **name**    | string | 被创建者的账户名            |
| **owner**   | string | 被创建者账户 owner 权限公钥 |
| **active**  | string | 被创建者 active 权限公钥    |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.newaccountSync({
    creator:'eosio',
    name:'NEW_ACCOUNT_NAME',
    owner:'PUBLIC_KEY_FOR_OWNER_PERMISSION',
    active:'PUBLIC_KEY_FOR_ACTIVE_PERMISSION'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.newaccount({
        creator:'eosio',
        name:'NEW_ACCOUNT_NAME',
        owner:'PUBLIC_KEY_FOR_OWNER_PERMISSION',
        active:'PUBLIC_KEY_FOR_ACTIVE_PERMISSION'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
});
```

## setcode

部署 JS 合约

### 参数

| name          | type   | description  |
| ------------- | ------ | ------------ |
| **account**   | string | 合约所属账户 |
| **vmtype**    | uint8  | 合约引擎类型 |
| **vmversion** | uint8  | 合约引擎版本 |
| **code**      | string | 合约代码 zip 打包后的 bytes |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});
let ctx = fibos_client.contractSync('eosio');

let r = ctx.setcodeSync({
    account: 'ACCOUNT_NAME',
    vmtype: 0,
    vmversion: 0,
    code: 'BYTES_OF_JS_CONTRACT_CODE',
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.setcode({
        account:'ACCOUNT_NAME',
        vmtype: 0,
        vmversion: 0,
        code: 'BYTES_OF_JS_CONTRACT_CODE'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
});
```



## setabi

部署 abi 文件

### 参数

| name        | type   | description  |
| ----------- | ------ | ------------ |
| **account** | string | 合约所属账户 |
| **abi**     | json   | abi 文件代码 |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

let r = ctx.setabiSync({
    account: 'ACCOUNT_NAME',
    abi: {"version":"eosio::abi/1.0","types":[],"structs":[],"actions":[],"tables":[],"ricardian_clauses":[],"error_messages":[],"abi_extensions":[],"variants":[]}
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.setabi({
        account:'iforedpacket',
        abi: {"version":"eosio::abi/1.0","types":[],"structs":[],"actions":[],"tables":[],"ricardian_clauses":[],"error_messages":[],"abi_extensions":[],"variants":[]}
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
});
```



## updateauth

增加或修改用户权限

### 参数

| name           | type   | description                    |
| -------------- | ------ | ------------------------------ |
| **account**    | string | 账户名称                       |
| **permission** | string | 已存在的权限或者新增的权限名称 |
| **parent**     | string | 创建该权限的父权限             |
| **auth**       | json   | 该权限的组成                   |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.updateauthSync({
  account: 'ACCOUNT_NAME',
  permission: 'owner',
  parent: '',
  auth: {
    threshold: 1,
    keys: [{
      key: 'PUBLIC_KEY_OF_ANOTHER_ACCOUNT',
      weight: 1
    }]
  }
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.updateauth({
        account: 'ACCOUNT_NAME',
        permission: 'owner',
        parent: '',
        auth: {
            threshold: 1,
            keys: [{
                key: 'PUBLIC_KEY_OF_ANOTHER_ACCOUNT',
                weight: 1
            }]
        }
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## deleteauth

删除权限

### 参数

| name           | type   | description  |
| -------------- | ------ | ------------ |
| **account**    | string | 账户名称     |
| **permission** | string | 需删除的权限 |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.deleteauthSync({
    account: 'ACCOUNT_NAME',
    permission: 'PERMISSION_NAME'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.deleteauth({
        account: 'ACCOUNT_NAME',
        permission: 'PERMISSION_NAME'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## linkauth

给权限指定 action

### 参数

| name            | type   | description |
| --------------- | ------ | ----------- |
| **account**     | string | 账户名称    |
| **code**        | string | 合约名称    |
| **type**        | string | action 名称 |
| **requirement** | string | 权限名称    |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.linkauthSync({
   account: 'ACCOUNT_NAME',
   code: 'CONSTRACT_NAME',
   type: 'ACTION_NAME',
   requirement: 'PERMISSION_NAME'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.linkauth({
        account: 'ACCOUNT_NAME',
        code: 'CONSTRACT_NAME',
        type: 'ACTION_NAME',
        requirement: 'PERMISSION_NAME'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## unlinkauth

删除权限可执行的 action

### 参数

| name        | type   | description |
| ----------- | ------ | ----------- |
| **account** | string | 账户名称    |
| **code**    | string | 合约名称    |
| **type**    | string | action 名称 |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.unlinkauthSync({
   account: 'ACCOUNT_NAME',
   code: 'CONSTRACT_NAME',
   type: 'ACTION_NAME'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.unlinkauth({
        account: 'ACCOUNT_NAME',
        code: 'CONSTRACT_NAME',
        type: 'ACTION_NAME'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## canceldelay

取消一个延迟交易

### 参数

| name               | type   | description |
| ------------------ | ------ | ----------- |
| **canceling_auth** | String | 权限类型    |
| **trx_id**         | String | 交易 hash   |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.canceldelaySync({
    canceling_auth: 'PERMISSION_LEVEL',
    trx_id: 'TRANSACTION_HASH'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.canceldelay({
        canceling_auth: 'PERMISSION_LEVEL',
        trx_id: 'TRANSACTION_HASH'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## buyrambytes

创建者调用该方法为被创建者购买内存来存放新账户的信息

### 参数

| name         | type   | description            |
| ------------ | ------ | ---------------------- |
| **payer**    | string | 创建者的账户名         |
| **receiver** | string | 被创建者的账户名       |
| **bytes**    | uint32 | 购买的内存大小（字节） |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.buyrambytesSync({
      payer: 'ACCOUNT_OF_PAYER',
      receiver: 'ACCOUNT_OF_RECEIVER',
      bytes: 4096
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.buyrambytes({
        payer: 'ACCOUNT_OF_PAYER',
        receiver: 'ACCOUNT_OF_RECEIVER',
        bytes: 4096
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## buyram

购买存储资源，区别是买特定数量的通证还是买特定大小的内容

### 参数

| name         | type   | description                |
| ------------ | ------ | -------------------------- |
| **payer**    | string | 购买存储资源的账号         |
| **receiver** | string | 接受存储资源的账号         |
| **quant**    | string | 购买存储资源所用的通证数量 |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.buyramSync({
      payer: 'ACCOUNT_OF_PAYER',
      receiver: 'ACCOUNT_OF_RECEIVER',
      quant: '0.1273 FO'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.buyram({
        payer: 'ACCOUNT_OF_PAYER',
        receiver: 'ACCOUNT_OF_RECEIVER',
        quant: '0.1273 FO'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```

## sellram

出售不需要的存储资源

### 参数

| name        | type   | description            |
| ----------- | ------ | ---------------------- |
| **account** | string | 出售资源通证的接受账号 |
| **bytes**   | uint64 | 出售多少空间的存储资源 |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.sellramSync({
      account: 'ACCOUNT_NAME',
      bytes: 789438000
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.sellram({
        account: 'ACCOUNT_NAME',
        bytes: 789438000
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## delegatebw

抵押通证获取 cpu 和带宽资源

### 参数

| name                   | type   | description                                |
| ---------------------- | ------ | ------------------------------------------ |
| **from**               | string | 资源抵押者的账户名                         |
| **receiver**           | string | 资源接受者的账户名                         |
| **stake_net_quantity** | string | 抵押者为接受者抵押 FO 获取 NET             |
| **stake_cpu_quantity** | string | 抵押者为接受者抵押 FO 获取 CPU             |
| **transfer**           | bool   | 代表抵押资源同时是否将对应通证转账给接受者 |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.delegatebwSync({
      from: 'ACCOUNT_OF_MORTGAGOR',
      receiver: 'ACCOUNT_OF_RECEIVER',
      stake_net_quantity: '3193.0000 FO',
      stake_cpu_quantity: '30000.0000 FO',
      transfer: 0
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.delegatebw({
        from: 'ACCOUNT_OF_MORTGAGOR',
        receiver: 'ACCOUNT_OF_RECEIVER',
        stake_net_quantity: '3193.0000 FO',
        stake_cpu_quantity: '30000.0000 FO',
        transfer: 0
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## undelegatebw

用来解除抵押，释放资源，收回通证

### 参数

| name                     | type   | description                    |
| ------------------------ | ------ | ------------------------------ |
| **from**                 | string | 解除用哪个账号所抵押的通证     |
| **receiver**             | string | 解除作用在哪个账号上的抵押通证 |
| **unstake_net_quantity** | string | 解除用来获取带宽资源的通证数量 |
| **unstake_cpu_quantity** | string | 解除用来获取计算资源的通证数量 |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.undelegatebwSync({
      from: 'ACCOUNT_OF_MORTGAGOR',
      receiver: 'ACCOUNT_OF_RECEIVER',
      unstake_net_quantity: '649540.0000 FO',
      unstake_cpu_quantity: '649540.0000 FO'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.undelegatebw({
        from: 'ACCOUNT_OF_MORTGAGOR',
        receiver: 'ACCOUNT_OF_RECEIVER',
        unstake_net_quantity: '649540.0000 FO',
        unstake_cpu_quantity: '649540.0000 FO'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## refund

在 undelegatebw 函数解除抵押后调用，作用是把抵押的通证退回账户

### 参数

| name      | type   | description  |
| --------- | ------ | ------------ |
| **owner** | string | 退回账户名称 |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.refundSync({
    owner: 'ACCOUNT_OF_OWNER'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.refund({
        owner: 'ACCOUNT_OF_OWNER'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## regproducer

注册成为区块生产者

### 参数

| name             | type   | description                  |
| ---------------- | ------ | ---------------------------- |
| **producer**     | string | 区块生产者账户名             |
| **producer_key** | string | 区块生产者公钥               |
| **url**          | string | 区块生产者宣传网站           |
| **location**     | uint16 | 区块生产者服务器位置地区代码 |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.regproducerSync({
    producer: 'ACCOUNT_OF_PRODUCER',
    producer_key: 'PUBLIC_KEY_OF_PRODUCER',
    url: 'https://fibos.io',
    location: 1
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.regproducer({
        producer: 'ACCOUNT_OF_PRODUCER',
        producer_key: 'PUBLIC_KEY_OF_PRODUCER',
        url: 'https://fibos.io',
        location: 1
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```

## unregprod

取消注册成为区块生产者

### 参数

| name         | type   | description |
| ------------ | ------ | ----------- |
| **producer** | string | 账户名称    |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.unregprodSync({
    producer: 'ACCOUNT_OF_PRODUCER'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.unregprod({
        producer: 'ACCOUNT_OF_PRODUCER'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## regproxy

注册成为代理人，接受其他用户的投票委托

### 参数

| name        | type   | description              |
| ----------- | ------ | ------------------------ |
| **proxy**   | string | 注册账户名称             |
| **isproxy** | bool   | 是否接受其他用户投票委托 |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.regproxySync({
    proxy: 'ACCOUNT_OF_PROXY',
    isproxy: 1
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.regproxy({
        proxy: 'ACCOUNT_OF_PROXY',
        isproxy: 1
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```



## voteproducer

给区块生产者进行投票

### 参数

| name          | type             | description |
| ------------- | ---------------- | ----------- |
| **voter**     | string           | 投票人      |
| **proxy**     | string           | 代理投票人  |
| **producers** | array of strings | 得票人列表  |

### 示例

fibos.js 环境下：

```javascript

const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.voteproducerSync({
    voter: 'ACCOUNT_OF_VOTER',
    proxy: 'ACCOUNT_OF_PROXY',
    producers: ['ACCOUNT_OF_PRODUCER1', 'ACCOUNT_OF_PRODUCER2']
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.voteproducer({
        voter: 'ACCOUNT_OF_VOTER',
        proxy: 'ACCOUNT_OF_PROXY',
        producers: ['ACCOUNT_OF_PRODUCER1', 'ACCOUNT_OF_PRODUCER2']
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```

备注：投票节点列表需要由开发者自己按照字母序排序，一次性最多可以给30个 BP 投票。



## claimrewards

区块生产者领取工资

### 参数

| name      | type   | description    |
| --------- | ------ | -------------- |
| **owner** | string | 区块生产者名称 |

### 示例

fibos.js 环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

let ctx = fibos_client.contractSync('eosio');

var r = ctx.claimrewardsSync({
    owner: 'ACCOUNT_OR_OWNER'
},{
    authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
});
console.log(r);
```

浏览器环境下：

```javascript
const FIBOS = require('fibos.js');

const fibos_client = FIBOS({
  // fibos 测试网 chainId
  chainId: '68cee14f598d88d340b50940b6ddfba28c444b46cd5f33201ace82c78896793a',
  keyProvider: 'PRIVATE_KEY', // 你的私钥
  httpEndpoint: 'http://api.testnet.fo',
});

fibos_client.contract('eosio').then((contract)=>{
    contract.claimrewards({
        owner: 'ACCOUNT_OR_OWNER'
    },{
        authorization: 'ACCOUNT_FOR_PRIVATE_KEY' // 私钥对应的账号
    })
})
```
