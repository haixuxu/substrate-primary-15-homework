# BTC UTXO

## 基本概念

UTXO (Unspent Transaction Output) 模型是比特币使用的一种交易记账方式。

每笔交易都包含输入和输出，输入是引用之前的UTXO，输出是生成新的UTXO。

## 工作原理

1. 创建新交易

   输入：新交易引入一个或者多个UTXO作为输入。

   输出：新交易生成一个或者多个新的UTXO作为输出，并且每个输出需要一个接受者地址和数量。

2. 验证交易

   - 验证UTXO是否存在和UTXO没有被使用。

   - 验证输入的签名是否为发送者或者有权使用UTXO。

   - 验证 输入的总数量=输出的总数量+交易费用。

3. 更新记录至区块链

​	新交易被网络节点验证后添加的区块链。

## 交易示例

> Alice 使用她的 1 BTC的 UTXO:	  [交易ID: tx1] + [索引: 0 ] + [Alice 的签名] + [金额: 1 BTC]
>
> Alice 拥有 1 BTC ， 想支付 0.5 BTC 给 Bob。

```makefile
输入 ：（当前示例中只有1个输入）
	输入 1:
    	[Alice 使用她的 1 BTC的 UTXO] + [Alice 的签名]

输出: （当前示例中包含2个输出）
	- 输出 1: [接收者地址: Bob 的地址] + [金额: 0.5 BTC]  
	- 输出 2: [接收者地址: Alice 的找零地址] + [金额: 0.5 BTC]
	
```

## 交易费用

交易费用是由输入和输出金额的差额决定的。矿工将这些交易费用作为奖励，激励他们验证和打包交易。

> Alice 拥有 1 BTC , 支付 Bob 0.5 BTC，输出金额总和为 0.5 BTC（给 Bob）+ 0.49 BTC（找零给 Alice），剩余的 0.01 BTC 作为交易费用支付给矿工。

```makefile
输入:
		[Alice 使用她的 1 BTC的 UTXO] + [Alice 的签名]
输出:
  - 输出 1:
    	[接收者地址: Bob 的地址] + [金额: 0.5 BTC]
  - 输出 2:
        [接收者地址: Alice 的找零地址] + [金额: 0.49 BTC]
        
交易费用: 0.01 BTC
```

