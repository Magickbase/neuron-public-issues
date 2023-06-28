# FAQ

### 什么是账户（Account）

对用来说，seed/master pri key 一组按照指定算法算出来的可操控的地址集合。

技术上来讲，一组按照指定算法算出来的地址。

通过Seed加一定规则（分层确定性钱包）生成的公钥（Public Key），再加上 lock 方法，生成的一组地址，即公钥和Lock约束衍生出来的地址集合。


### 什么是 Account ID

账户ID特指用户助记词的第一个root的hash值。账户ID用于为用户提供区分属于一套助记词/根私钥的地址和非属于一套助记词/根私钥的地址。

### 什么是交易方法（Payment method）

交易方法是为了标识CKB交易中交易类型的标签。与部分基于账户模型区块链中的交易不同，CKB中的交易方法是根据用户操作的Cell的Lock Hash进行的Tag标记，这种标记是链下解析的。

### 什么是交易的描述（Description）

在CKB中，交易的描述（Description）是指交易中包含的任意文本的字段，用于提供关于交易目的或其他相关信息的描述性信息。描述字段是可选的，它可以用来提供有关交易的额外信息，例如交易的用途、备注、标签等。

### 什么是Locktime

在CKB中，Locktime（锁定时间）是指一个交易的锁定时间戳。它是一个用于控制交易何时可以被确认和执行的机制。每个交易都可以设置一个Locktime值，该值可以是一个绝对时间戳或一个相对于当前块高度的值。

当一个交易被创建时，它可能会被设置一个Locktime，以指定在未来的某个时间或块高度之前，该交易不可被确认和执行。这可以用于实现一些特定的交易逻辑，例如延迟支付、条件付款等。

在达到指定的Locktime之前，交易被认为是不可用的，不会被矿工包含在区块中。一旦达到了指定的Locktime，交易就可以被确认和执行。

Locktime在CKB中是可选的，不是所有的交易都需要设置Locktime。它提供了一种灵活的方式来控制交易的执行时间，增加了CKB的功能和应用场景的多样性。

### 为什么 一笔交易中有多个to 地址？
CKB的交易是基于UTXO的交易模型，在该模型中，一笔交易的输入与输出均可能有多个。

同时一笔交易中，每一个输出地址都含有 “Data”和“Witness”字段。

### 关于Dapp request auth 与Lock Hash的请求

Lock Hash是Dapp request auth 的hash，因此是唯一确认的方法名。第三方可以通过提交PR，向协议注册新的Dapp Auth。

### 关于Dapp 与Lock Hash的请求

- 关于Lock Hash：
    当dapp 请求LockHash的方法中无参数时，Dapp默认请求全部的Lock Hash；当参数中含有 Lock Hash时，Dapp请求其指定的Lock Hash。

- 关于错误返回：
    - Panic when the user declines.
    - Panic immediately if the wallet does not support the requested DappAuth from the Dapp.



### 热钱包与观察钱包 与 dapp 的交互规则
> 离线钱包场景：在当前需求优先级下，我们认为热钱包连接dapp使用的场景更广；此外，出于XX考虑，dapp 直接连接离线钱包使用的场景不被考虑在此范围内。若要使用离线钱包，离线钱包应与一个热钱包搭配使用。因此，在使用离线钱包的情况下，离线钱包将被视作一个观察钱包。
- 当钱包连接网络与dapp交互时，其交互流程见[此链接](https://github.com/Magickbase/neuron-public-issues/issues/148)
- 当钱包用作观察钱包时，观察钱包可与dapp建立连接以获取相关数据，但无法进行转账操作。


### 为什么Lock Hash(dapp Auth)字段是必需的？
限制dapp对dapp Auth的访问有助于最小化用户信息的暴露。

每个衍生的公钥只使用一次，对应于特定的Lock类型，确保地址之间不能相互转换。如果应用的业务逻辑只需要使用A和B类型的地址，那么就不需要获取C类型的地址。通过授权锁定类型，可以防止将C类型地址暴露给DApp，从而减少用户信息的暴露。

还有可能应用程序同时支持A和B类型的地址，但用户可能不想使用B类型的地址。在这种情况下，用户可以编辑授权以限制应用程序仅使用A类型地址来完成业务逻辑。

### dapp Auth字段如何保护用户的隐私？

例如，考虑一个显示资产并需要访问用户所有地址的聚合dapp。然而，用户可能不希望将所有信息暴露给这个特定的dapp。

在当前设计中，dapp Auth字段是一个必需字段，而钱包对dapp的响应是可选的。因此，响应是必要的，并且在命名空间协议中，当dapp请求授权时，它会包含每个请求字段的具体值（例如支持的方法、事件监听器、锁定类型）。钱包会根据自身实现为相应的字段返回支持的值（方法、事件通知、锁定类型），而锁定类型则取决于用户的授权。

在请求授权时，Dapp 应首先调用 ckb_getSupportedLockTypes 方法以获取支持的锁定类型范围。如果钱包返回的锁定类型范围不支持 Dapp 的业务逻辑，则 Dapp 不应请求授权。相反，它应向用户提示原因。Dapp 应清楚地了解自己的需求并将其传达给钱包。