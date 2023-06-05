# CKB General Component for WalletConnect

## General Component for Wallet Side

A general component is provided for WalletConnect on the side of third party wallet.

### Related isssues


### Connecting flowchart

> Scanning QR code is the most used and also recommended for users to connect to dApp with your wallet. We also offer a way to connect by pasting the WalletConnect code which could be used for testing. [UI for Connecting Flowchart](https://www.figma.com/file/6XNoimRDbFTTNm016rbIdU/Magickbase?type=design&node-id=16072-38648&t=rF3mLzNYeaveGD6Q-0)

#### UI Sketch

![UI图](pic/2023-05-30-09-20-22.png)

#### Status1: Unconnected

While the dapp is unconnected with the wallet, users can click on the button below to scan QR code on the dapp side in order to connect the dapp.

![UnconnectStatus](pic/2023-05-30-08-19-27.png)

#### Status2: Connecting

After clicking the scan button, and if the QR code is correct then the dapp and wallet are trying to communicate following the protocol. If the QR code is not in correct format, corresponding messages will be popped up.

![ConnectingStatus](pic/2023-05-30-08-22-37.png)

#### Status3: Connect Request

Once the WalletConnection information fecthes back, the wallet shows the connection request information, including the dapp name, its url, network, Account and Auth.

- The network refers to the CKB network to which the dapp is going to connect.
- The Account refers to the CKB wallet account that the user is going to use.
- The Auth refers to the lock method for user addresses. Typically, a user's addresses can be divided into different adress sets based on the lock method they use, and here various classification methods are provided. Dapps can request the specific address sets they need, and users can choose to revoke authorization for certain address sets.

To cancel this request, just press the Reject button.

![ConnectRequest](pic/2023-05-30-08-42-31.png)

#### Status4: Connectting Information

After the connection is established, the dapp will maintain a persistent connection with the wallet. The relevant connection information, the confirmed information from the previous step, will still be displayed here. Users can disconnect from the dapp at any time.

![ConnecttingInformation](pic/2023-05-30-08-41-25.png)

### Signing Tx flowchart
![picture 1](pic/967d539ec2b15727f459b9e33a70d0630de6a63f58e57e93ffe197de29380c01.png)  
When dApp initializes a transaction, this component will pop up/ show.
[UI for Signing Tx flowchart](https://www.figma.com/file/6XNoimRDbFTTNm016rbIdU/Magickbase?type=design&node-id=16536-38593)
#### To confirm/reject a transaction from dapp

- Normally, if the user want sign the transaction by simply click the NEXT btn then click CONFIRM btn.
![picture 2](pic/f1d509997ae20bdb51032484bb33e5b704acdcef581fd53c7280b66747f5a54b.png)  

- To reject or cancel this transaction , you can click REJECT Btn
on the first step.


#### To modify the transaction information

- Click the pencil like icon
![picture 3](pic/dde9d7d213ce52ce6b1f9febcfc2585cc743ff7ac0d0938cbcd64de595092660.png)  

- Then modify information in corresponding text field, and click NEXT to continue.

#### Further examine the receiving address and its detailed data

- Click the arrow next to the address. The Data and Witness will display(elaborately speaking, these details will move upwards)
![picture 4](pic/70d8140d96601991d8aa2632fc65d0c2a1eccef17ed02505fe50b9adade86115.png)  
- In the UI demo, click this arrow, users can view all the receiving addresses, then view the data and witness the one you want by click the arrow next to the address on list.
![picture 5](pic/095d5fa9970726f93dc8265cf2eb24fad2f908788456ad50ba6aef20558c5ad7.png)  
