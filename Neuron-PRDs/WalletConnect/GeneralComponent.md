# CKB General Component for WalletConnect

## 1 General Component for Wallet Side

A general component is provided for WalletConnect on the side of third party wallet.

### 1.1 Connecting flowchart


> Scanning QR code is the most used and also recommended for users to connect to dApp with your wallet. We also offer a way to connect by pasting the WalletConnect code which could be used for testing. [UI for Connecting Flowchart](https://www.figma.com/file/6XNoimRDbFTTNm016rbIdU/Magickbase?type=design&node-id=16072-38648&t=rF3mLzNYeaveGD6Q-0)

#### 1.1.1 Corresponding functions and Labels
All the labels and functions which are used to construct the the prototype are listed if you'd like to integrate them into your app in your own way.

|Flow|Name|Type|Requirement Levels|Note|
| -- | -- | -- | -- | -- |
|Connecting flow|Scan WalletConnect QR code|Function|MUST|--|
| Connecting flow | Connect by WalletConnect-code | Function | SHOULD NOT | Supposed to be only used for testing |
| Connecting flow | link | Label | MUST | The URL of the dapp |
| Connecting flow | Network | Label | MUST | The network of current CKB blockchain |
| Connecting flow | Account | Label | MUST | The account user is using on wallet. |
| Connecting flow | dApp request auth | Label | MUST | This means the lock method for user address sets that dapp would like to get access to. |
| Connecting flow | Disconnect | Function | MUST | -- |

![picture 15](pic/94530b52afa6429307f833788acdeafac4ac9f7a47b5ef3f4d036450ac59c339.png)  



#### 1.1.2 Status1: Unconnected

While the dapp is unconnected with the wallet, users can use scan WalletConnect QR code function in order to connect the dapp.

![picture 13](pic/48847073e04b228469105ff5be086e6d2f4fe1e95aa511036bd0b30d3d253762.png)  


#### 1.1.3 Status2: Connecting

To do so, users are always supposed to click a scan button, and if the QR code is correct then the dapp and wallet are trying to communicate following the protocol. If the QR code is not in correct format, corresponding messages will be popped up.

![picture 14](pic/49c0c0fa7f44791fce1d00a4b952daf8f21b2375c0670e70667625fcd698552e.png)  


#### 1.1.4 Status3: Connect Request

Once the WalletConnection information fecthes back, the wallet shows the connection request information, including the dapp name, its url, network, Account and Auth.

- The network refers to the CKB network to which the dapp is going to connect.
- The Account refers to the CKB wallet account that the user is going to use.
- The Auth refers to the lock method for user addresses. Typically, a user's addresses can be divided into different adress sets based on the lock method they use, and here various classification methods are provided. Dapps can request the specific address sets they need, and users can choose to revoke authorization for certain address sets.

To cancel this request, just press the Reject button.

![ConnectRequest](pic/2023-05-30-08-42-31.png)

#### 1.1.5 Status4: Connectting Information

After the connection is established, the dapp will maintain a persistent connection with the wallet. The relevant connection information, the confirmed information from the previous step, will still be displayed here. Users can disconnect from the dapp at any time.

![ConnecttingInformation](pic/2023-05-30-08-41-25.png)

### 1.2 Signing Tx flowchart

#### 1.2.1 Corresponding functions and Labels
|Flow|Name|Type|Requirement Levels|Note|
| -- | -- | -- | -- | -- |
| Send transaction | Payment method | Label | SHOULD | Currently, the CKB transactions are all TRANSFER. |
| Send transaction | To Address List | Label | MUST | -- |
| Send transaction | Fee Rate | Label | MUST | -- |
| Send transaction | Description | Label | MUST | -- |
| Send transaction | Locktime | Label | MUST | -- |
| Send transaction | Recieve Amount for individual address | Label | MUST | This refers to the amounts that every individual address will receive |
| Send transaction | Transaction Info Modify | Function | MUST | Users are able to modify or adjust some data in the transaction like Fee Rate |
| Send transaction | Transaction Data for individual address | Label | MUST | -- |
| Send transaction | Witness for individual address | Label | MUST | -- |
| Send transaction | Decode Data for individual address | Function | SHOULD | The individual data could be decoded for easier reading, however, different sources have been given for users/wallet to choose. |


When dApp initializes a transaction, this component will pop up/ show.
[UI for Signing Tx flowchart](https://www.figma.com/file/6XNoimRDbFTTNm016rbIdU/Magickbase?type=design&node-id=16536-38593)

#### 1.2.2 To confirm/reject a transaction from dapp

- Normally, if the user want sign the transaction by simply click the NEXT btn then click CONFIRM btn.
![picture 6](pic/23e6295e43fe3438469a801e02511285524c90e09fc6a72c1eac1c54b93a3659.png)  


- To reject or cancel this transaction , you can click REJECT Btn
on the first step.


#### 1.2.3 To modify the transaction information

- Click the modify icon
![picture 9](pic/1f89dee53485fa9914341c9421b51588f81999f525a6dcc7821f22d1ab5865e9.png)  


- Then modify information in corresponding text field, and click NEXT to continue.

#### 1.2.4 Further examine the receiving address and its detailed data

- Go to the individual address detail pages. 
![picture 11](pic/5c000b5c7cdbbc16d8653dfae8a15a3f113f77477eee070c0bec285066637291.png)  

- To decode the Data and Withness with data of different source.

### 1.3 While wallet is offline

When the wallet is offline, and the DAPP wants to generate and use multiple wallet addresses. 

At this point, the user can choose to either connect the wallet to the blockchain network or authorize the wallet to generate addresses.

![picture 18](pic/50abf7db993b5d53336d6035584e9cc1a05af8ace4ee0a241b7ae6f5b2519bd9.png)  
