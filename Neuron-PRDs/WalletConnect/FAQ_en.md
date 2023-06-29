# FAQ

### What is Account

For users, an account is a collection of addresses derived from a set of mnemonics or root private keys according to a specified algorithm.

Technically, it refers to a set of addresses derived using a specified algorithm. It involves generating a public key (Public Key) by adding a seed with certain rules (hierarchical deterministic wallet), and then combining it with a lock script to create a set of addresses. These addresses are derived based on the combination of the public key and lock script constraints.

### What is Account ID

Account ID specifically refers to the hash value of the first root of the user's mnemonic words. Account ID is used to distinguish addresses belonging to a set of mnemonic words/root private keys from addresses that do not belong to them. User interactions with the blockchain do not directly involve the Account or Account ID.

### What is Lock Hash？

Lock Hash is the hash value derived from the code hash in the lock script, the hash type in the lock script, and the arguments in the lock script.

For users, the Lock Hash does not reveal the corresponding business logic. Therefore, when a dapp requests a set of addresses, it typically exposes the code hash in the lock script as a readable field in the Dapp Request Auth. The mapping table between Dapp Request Auth and Lock Hash will be updated on a third-party platform.

### What is Payment method
A Payment Method is used to identify the label of a transaction type in the CKB transaction. Unlike transactions in some account-based blockchain models, the mentioned payment method is a tag based on the Lock Hash of the Cell transfered by the user. Currently, this tag is resolved off-chain to provide readability for users to understand transaction differences.

### What is a Description

In CKB, the Description of a transaction refers to the field that contains arbitrary text within the transaction. It provides descriptive information about the transaction's purpose or other related details. The description field is optional and can be used to provide additional information about the transaction, such as its purpose, notes, or labels.

### What is Locktime

In CKB, Locktime refers to the locking timestamp of a transaction. It is a mechanism used to control when a transaction can be confirmed and executed. Each transaction can set a Locktime value, which can be an absolute timestamp or a value relative to the current block height.

When a transaction is created, it may be assigned a Locktime to specify that the transaction cannot be confirmed and executed until a certain time or block height in the future. This can be used to implement specific transaction logic, such as delayed payment or conditional payments.

Until the specified Locktime is reached, the transaction is considered unspendable and will not be included in blocks by miners. Once the specified Locktime is reached, the transaction can be confirmed and executed.

Locktime is optional in CKB, and not all transactions need to set a Locktime. It provides a flexible way to control the execution time of transactions, increasing the functionality and diversity of CKB's applications.

### Why are there multiple "to" addresses in a transaction?
CKB transactions are based on the UTXO (Unspent Transaction Output) model, where a transaction can have multiple inputs and outputs.

In a transaction, each output address contains the "Data" and "Witness" fields.

### About Dapp and Lock Hash Requests
- About Lock Hash:
    When a Dapp requests the Lock Hash method without any parameters, the Dapp defaults to requesting all Lock Hashes. When the parameters include a Lock Hash, the Dapp requests the specified Lock Hash.

- About error responses:
    - Panic when the user declines.
    - Panic immediately if the wallet does not support the requested DappAuth from the Dapp.

### Interaction rules between Hot Wallets, Observer Wallets, and Dapps

> Offline Wallet Case: Considering the current priority of demands, we believe that the case of hot wallets connecting to Dapps is more common. Therefore, the interaction entities in this protocol are "hot wallets" and "Dapps". The case where Dapps directly connect to offline wallets is not considered within the scope of this protocol. If you want to use an offline wallet, it should be used in conjunction with a hot wallet. Therefore, when using an offline wallet, it will be treated as an observe wallet.

- When a wallet connects to the network and interacts with a Dapp, the interaction process can be found at [this link](https://github.com/Magickbase/neuron-public-issues/issues/148).
- When a wallet is used as an observe wallet, it can establish a connection with a Dapp to retrieve relevant data.

### Why is the dapp Auth field necessary? 

Limiting Dapp's access to the dapp Auth field helps minimize the exposure of user information.

Each derived public key is used only once and corresponds to a specific lock type, ensuring that addresses cannot be converted between each other. If the application's business logic only requires the use of A and B type addresses, there is no need to obtain C type addresses. By authorizing the lock type, the exposure of C addresses to the DApp is prevented, reducing the exposure of user information.

It is also possible that the application supports both A and B type addresses, but the user prefers not to use B type addresses. In this case, the user can edit the authorization to restrict the application to only use A type addresses to complete the business logic.

### How does dapp Auth field protect the privacy for users?


For example, consider an aggregation dapp that displays assets and requires access to all of a user's addresses. However, the user may not want to expose all of their information to this particular dapp.

In the current design, the dapp auth field is a MUST field, while the wallet's response to the dapp is optional. Therefore, it is necessary to respond, and in the namespace protocol, when a dapp requests authorization, it includes specific values for each requested field (such as supported methods, event listeners, lock types). The wallet will respond with supported values for the corresponding fields (methods, event notifications, lock types) based on its implementation, and the lock types will depend on user authorization.

For instance, when the dapp requests authorization with lockTypes [secp256k1, acp], the wallet's UX will display [x] secp256k1, [x] acp, [ ] omnilock. Based on the wallet's personalized design, if the user cancels the selection of acp and agrees, the wallet will return lockTypes: [secp256k1]. The wallet will remind the user of the supported/unsupported functionalities based on the user's authorization information.

When requesting authorization, the dapp should first call ckb_getSupportedLockTypes to obtain the supported lock types range. If the wallet's returned lock range does not support the business logic of the dapp, the dapp should not request authorization. Instead, it should prompt the user with the reason. The dapp should have a clear understanding of its own requirements and communicate them to the wallet.

### Why dapp Auth field is MUST rather than SHOULD

If the dapp does not specify the lock range, there will be a confusing flow when the dapp's process design is not well thought out:

1. The dapp blindly requests addresses for all lock types.
2. The wallet returns addresses for all types.
3. The dapp realizes that it doesn't need all the addresses.
4. The user becomes confused, authorizes the request, but cannot perform any further operations.

To avoid this flow, it is recommended to require the dapp to specify the lock range when requesting authorization. This can be achieved by providing a method in the SDK to fetch all addresses. When the dapp calls the SDK, it will explicitly understand the purpose of this method and have better control over the address retrieval process.
