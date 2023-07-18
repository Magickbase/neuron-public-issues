# Neruron Wallet


## Download & Installation

1.Download Address:https://github.com/nervosnetwork/neuron/releases
2.Select the desired version (the latest version is recommended) and the matching system installer to download.
3.Verify that the downloaded installation package is not hooked according to SHA256 Checksum.
4.Unzip or install neuron wallet.


## Usage

### Create or Import a wallet

#### Create
1.Generate wallet seed
2.Manually enter wallet seed and verify

#### Import

1.Import Wallet Seeds
2.Import from Keystore
3.Import Harware Wallet

#### Wallet Account Setup

1.Name the wallet
2.Set Password

### Blocks synchronization
1.Set the node data path
2.Set the index data path
3.Finding predefined trusted block
4.Automatically synchronizes block data

>To be updated
>### Overview
>1.Balance:Displays the full current wallet balance (needs to be synchronized to the latest block)
>2.Send&Recive:Click to make an on-chain transaction
>3.Recent activities:Display recent transaction history and details
>
>### Send&Receive
>1.Send：Initiate on-chain transactions
>- Send to:Adding an address on the CKB chain for transactions
>- Amount:Enter the amount to be sent, optionally click MAX to enter the maximum value automatically.
>- Add a address:Adding additional CKB on-chain addresses for transactions
>- Set lock time:Set the lock time of the transaction, which may be inaccurate due to the uncertainty of the block out time.
>- Description:Add description to this transaction
>- Transaction Fee:Displays estimated transaction costs based on current transactions and on-chain data.
>- Price:Select recommended rate or customized rate, default customized rate supports selection of slow/standard/fast.
>- Submit Transaction:Submits transactions after verifying passwords and provides the ability to export transactions.
>
>2.Receive:Receive on-chain transfers
>- Address QR code：Provides a QR code image of the current address and offers download and copy functions.
>- Address：Displays the receiving address under the current wallet, with the new address selected by default to ensure user privacy and security.
>- Toggle Address Format：Displays the full address by default and provides the ability to switch to a deprecated address format.
>- Address Book：Displays the receiving address and change address under the current wallet, providing the ability to copy the address or balance.
>- Hardware wallet:Provides the ability to verify the address when using a hardware wallet (requires connection to the wallet)


### History
1.Search:Search for Tx hash, address, or date to find the transaction.
2.Export:Export transaction history in csv format.
3.Transaction List
- Type:Display the type of transaction.
- Amount:Displays the amount received and spent for the current transaction.
- Time:Displays the date and time of the transaction (accurate to the second)
- Status:Displays the on-chain status of the transaction.
- Operation:Expand or collapse the information of the transaction.
- View Details:Provides the ability to view transaction details in the expanded state and supports opening in a explorer.
4.Transaction Details
- Basic Information:Displays the transaction hash, block number, date, and income.
- Inputs and outputs:Displays the input and output parameters of the transaction.

### Nervos DAO
1.Account Info:Displays the available account balance, locked amount, and current APC.
2.Deposit:Click to initiate a transaction to deposit into the Nervos DAO.
3.Deposit and completed list:Displays deposited and completed transactions for Nervos DAO.

### Settings
1.Wallet:Switch the current wallet account.
2.General
- Version:Displays the current version and offers to check for updates.
- Language:Select language, currently supports English and Chinese.
>To be updated
>
>3.Network:Select the network node used by the wallet.
4.Data:Selects data storage paths for nodes and indexes as well as providing cache cleanup.

### Experimental

#### Customized Assets
1.Synchronization：Full node mode synchronization needs to be completed before all custom assets can be displayed.
2.Customized Asset List
- Time:Displays the time when the asset was traded and uses this to sort the list (from late to early).
- Asset:Displays the name of the identified asset and the unidentified displays the unknown asset.
- Operation:Support claim, transfer, withdraw, and migrate assets as well as check transaction details.(Locked assets and unidentified assets not available for claim)

#### Assets Accounts
1.Search:Search for the account name, token name, or symbol.
2.Create an asset account：Create a sUDT or CKB account to accept customized assets.
3.Account List：Displays the custom asset accounts that have been added.

### Wallet connect

### Dark Mode
Change the theme color of the software by clicking the top icon to switch to dark mode.

>To be updated
>### Light Client Mode
>Light Client Mode is a connection mode for Neuron that can be realized by connecting to the built-in CKB Light Client node through the network settings in the settings. It downloads a portion of the blockchain data to >get the necessary information compared to a full node. This allows Neuron to access the CKB blockchain faster.





 
