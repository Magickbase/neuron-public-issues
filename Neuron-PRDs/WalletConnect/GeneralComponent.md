# CKB General Component for WalletConnect

## 1 General Component for Wallet Side

A general component is provided for WalletConnect on the side of third party wallet.

### 1.1 Connecting flowchart


> Scanning QR code is the most used and also recommended for users to connect to dapp with your wallet. We also offer a way to connect by pasting the WalletConnect code which could be used for testing. [UI for Connecting Flowchart](https://www.figma.com/file/6XNoimRDbFTTNm016rbIdU/Magickbase?type=design&node-id=16072-38648&t=rF3mLzNYeaveGD6Q-0)

#### 1.1.1 Corresponding functions and Labels
All the labels and functions which are used to construct the the prototype are listed if you'd like to integrate them into your app in your own way.

|Flow|Name|Type|Requirement Levels|Note|
| -- | -- | -- | -- | -- |
|Connecting flow|Scan WalletConnect QR code|Function|MUST|--|
| Connecting flow | Connect by WalletConnect-code | Function | SHOULD NOT | Supposed to be only used for testing |
| Connecting flow | link | Label | MUST | The URL of the dapp |
| Connecting flow | Network | Label | MUST | The network of current CKB blockchain |
| Connecting flow | Account | Label | MUST | The account user is using on wallet. |
| Connecting flow | dapp request auth | Label | MUST | This means the lock method for user address sets that dapp would like to get access to. [Why this is necessary？](/Neuron-PRDs/WalletConnect/FAQ.md)|
| Connecting flow | Disconnect | Function | MUST | -- |

![picture 19](pic/e2a5e75d21dbe79380ac1e27264665cde5538d82ad866eab0d7b58640eeb2128.png)  



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
- The Auth refers to the lock method for user addresses. Typically, a user's addresses can be divided into different adress sets based on the lock method they use, and here various classification methods are provided. dapps can request the specific address sets they need, and users can choose to revoke authorization for certain address sets.

To cancel this request, just press the Reject button.

![ConnectRequest](pic/2023-05-30-08-42-31.png)

#### 1.1.5 Status4: Connectting Information

After the connection is established, the dapp will maintain a persistent connection with the wallet. The relevant connection information, the confirmed information from the previous step, will still be displayed here. Users can disconnect from the dapp at any time.

![ConnecttingInformation](pic/2023-05-30-08-41-25.png)

### 1.2 Signing A Message
When a dapp requires the user to perform a signature operation, it can be done through a signature information flow.

|Flow|Name|Type|Requirement Levels|Note|
| -- | -- | -- | -- | -- |
| Signing A Message | link | Label | MUST | The URL of the dapp |
| Signing A Message | Network | Label | MUST | The network that dapp wants the user to sign on |
| Signing A Message | Message | Label | MUST | The message that dapp wants the user to sign with|

Based on the Connected state, the dapp will send a signature request to the wallet. Users can choose to sign or not sign the request on the wallet.

![picture 21](pic/96aee7deb483263acd18b2485f54ca69f802fd14d86bcc7bf86e33d1d9b09f62.png)  

Users should be familiar with, understand, and trust the content of their signature before proceeding.


### 1.3 Signing Tx flowchart

#### 1.3.1 Corresponding functions and Labels
|Flow|Name|Type|Requirement Levels|Note|
| -- | -- | -- | -- | -- |
| Send transaction | link | Label | MUST | The URL of the dapp |
| Send transaction | Network | Label | MUST | The network that dapp wants the user to sign on |
| Send transaction | Payment method | Label | SHOULD | Currently, the CKB transactions are all TRANSFER. |
| Send transaction | To Address List | Label | MUST | -- |
| Send transaction | Fee or Fee Rate | Label | MUST | -- |
| Send transaction | Description | Label | MUST | -- |
| Send transaction | Locktime | Label | OPTIONAL | -- |
| Send transaction | Recieve Amount for individual address | Label | MUST | This refers to the amounts that every individual address will receive |
| Send transaction | Transaction Info Modify | Function | MUST | Users are able to modify or adjust some data in the transaction like Fee Rate |
| Send transaction | Transaction Data for individual address | Label | MUST | -- |
| Send transaction | Witness for individual address | Label | MUST | -- |
| Send transaction | Decode Data for individual address | Function | SHOULD | The individual data could be decoded for easier reading, however, different sources have been given for users/wallet to choose. |
| Send transaction | Transaction Raw Data  | Label | SHOULD | Transaction Input will be displayed for professional users or any advanced usage. Through the transaction raw data, users can understand the inputs and outputs associated with this transaction.|

When dapp initializes a transaction, this component will pop up/ show.
[UI for Signing Tx flowchart](https://www.figma.com/file/6XNoimRDbFTTNm016rbIdU/Magickbase?type=design&node-id=16536-38593)

#### 1.3.2 To confirm/reject a transaction from dapp

- Normally, if the user want sign the transaction by simply click the NEXT btn then click CONFIRM btn.
![picture 22](pic/97ab3debd332737cd47bb08d6a3c6e84a902c3db546ccbb13372435f68ca8bdb.png)  


- To reject or cancel this transaction , you can click REJECT Btn
on the first step.


#### 1.3.3 To modify the transaction information

- Click the modify icon
![picture 24](pic/00bc84a1bbd7e7bf4250cf73cf1c9b68104bf9d97296910bffd2adfe92b96c1a.png)  


- Then modify information in corresponding text field, and continue.

#### 1.3.4 Further examine the receiving address and its detailed data

- Check more addresses and go to the individual address detail pages. 
![picture 25](pic/c3648acc2c75e30a16dd9d169b60b626614acd955ef4708e59a4df52c4ac2d40.png)  

- To decode the Data and Withness with data of different source.

### 1.4 While wallet is offline

When the wallet is offline, and the dapp wants to generate and use multiple wallet addresses. 

At this point, the user can choose to either connect the wallet to the blockchain network or authorize the wallet to generate addresses.

|Flow|Name|Type|Requirement Levels|Note|
| -- | -- | -- | -- | -- |
| Offline usage | link | Label | MUST | The URL of the dapp |
| Offline usage | Network | Label | MUST | The network that dapp wants the user to sign on |
| Offline usage | Number | Label | MUST | The nember of addresses that the dapp wants to generate|
| Offline usage | Description | Label | MUST | The description why the dapp wants to generate |

![picture 26](pic/b715770fd1cdf0d619d97e40aef34eb8844ce852c97142a7d24e05dd70657f0e.png)  

