# A process and a dataflow of how Neuron/JoyID work with this protocol
In order to locate and describe the Account issue we may face while using this protocol, A process and dataflow of how Neuron/JoyID work with this protocol is considered a case to talk with.

To solve this problem, a Dapp demo and its UX protocol will be proposed below to demonstrate how the dapp communicates with wallet by this protocol.
# An Dapp demo for showing how wallet connect protocol working.

This is a Dapp demo which designed to demonstrate how this protocol facilitates connections. Users can connect to this Dapp through WalletConnect. Once connected, users can like articles and donate to the author using CKB.

![pic 2](pic/DappHomePage.png)  

# UX protocol & involving field

In this section, the flow and involved field will be demonstrated to show how the protocol work.

## Establish connection

While not log in , users will see the page like this.
![pic 1](pic/NotLogIn.png)  

| Flow | Name | Type | Requirement Levels | Note |
|------|------|------|--------------------|------|
| Connecting flow | WalletConnect Option and WalletConnect QR code | Function | MUST | -- |
| Connecting flow | Notes | Label | SHOULD | Show the user which network is requested to connect and which address sets(dApp request auth) are request in advance |

<!-- 问题：是否验证地址集合中所有地址属于当前用户？ -->
<!-- 问题：同一个私钥 使用metamask登录（kecake?）的/和neuron（加密算法...）登录的需要是同一个用户吗？ （根据定义，可以不需要）-->
<!-- 用户身份的绑定是 地址？公钥？ -->
<!-- 唯一索引是地址？公钥？-->

<!-- 问题：当用户Like时，同一个私钥的身份如何被绑定，现在同一个私钥可能生成2个公钥，以至于身份不被确定 -->
<!-- 假如是同一个私钥，有2个钱包(【曲线】R1?K1？ [HD：Path] ACP? K1?) -->
<!-- 做identity 验证行不通 -->

<!-- 用户身份的绑定是 地址？公钥？ 使用Account -->
<!-- dapp 白名单登录（有一个地址有权限）：文章就能看 -->
<!-- dapp 合并Cell 转账（所有地址）-->

<!-- 建立连接时Account身份验证？Identity 如何设计。HD钱包如何设计？非HD钱包如何设计-->
<!-- Case：HD登录（HD钱包的identify可以是什么），非HD登录也OK（非HD钱包的identify可以是什么）-->
<!-- 登录成功的定义：两次登录被识别为相同的身份 -->

<!-- 产品层面登录成功的定义：如果用同一种（算法）钱包，同一Seed登录，被识别为相同的身份；如果用不同（算法）钱包，同一Seed登录，可以不被识别为相同的身份； -->
<!-- 问题：同一个私钥 使用metamask登录（kecake?）的/和neuron（加密算法...）登录的需要是同一个用户吗？ （根据定义，可以不需要）-->

<!-- To do: 协议层面 + UX -->
<!-- 协议层面: -->
<!-- UX层面:在身份定义确认后，修改对应General Component UX protocol -->

## HomePage

After logged in, Some account info and dapp functions will be provided to users. 

![pic 1](pic/Homepage.png)  
| Page | Name | Type | Requirement Levels | Note |
|------|------|------|--------------------|------|
| HomePage | AcountID | Function | MUST | - |
| HomePage | Network | Label | MUST | Show the user which network is requested to connect and which address sets(dApp request auth) are request in advance |
| HomePage | Disconnet | Function | MUST | The Disconnect function demonstrate how user initial a disconnection on the dapp side. |
| HomePage | Asset | Label | SHOULD NOT | This part info demonstrate how to display info of an Account, but ADDRESS should not be displayed to user due to ACCOUNT is already defined and put forward.   |
| HomePage | Like | Function | SHOULD | The Like function in this case demonstrate how dapp request user to sign message with an Account. |
| HomePage | Donate | Function | SHOULD | The Donate function in this case demonstrate how dapp request user to sign a transaction with an Account. |


### Asset Info

In this dapp, Connected account’s CKB will be shown to user.
First, the dapp **define** the CKB of an account is **the total CKB amount of all addresses in the address set** provided by wallet during connection.

### Like Function
By clicking the Like button, a window will pop up to ask user to confirm ,users are requested to sign a message on his CKB wallet which is connected in the previous connecting part to verify that this account belongs to him.

![pic 2](pic/LikeConfirmWindow.png)  

### Donate Function
By clicking the donation amount, a donation window will pop up to ask user to confirm ,users are requested to sign a transaction on his CKB wallet which is connected in the previous connecting part to send fixed amount CKB to a fixed address.

![pic 3](pic/DonationWindow.png)  
