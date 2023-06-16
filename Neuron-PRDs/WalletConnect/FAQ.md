# FAQ


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
