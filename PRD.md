# Neruron Wallet


## Download & Installation

1. Download Address:https://github.com/nervosnetwork/neuron/releases
2. Select the desired version (the latest version is recommended) and the matching system installer to download.
3. Verify that the downloaded installation package is not hooked according to SHA256 Checksum.
4. Unzip or install the neuron wallet.


## Usage

### Create or Import a wallet

#### Create
1. Generate wallet seed
2. Manually enter the wallet seed and verify

#### Import

1. Import Wallet Seeds
2. Import from Keystore
3. Import Hardware Wallet

#### Wallet Account Setup

1. Name the wallet
2. Set Password

### Blocks synchronization
1. Set the node data path
2. Set the index data path
3. Finding a predefined trusted block
4. Automatically synchronizes block data

### Menu Bar
1. Wallet: Manage the wallet and perform operations.
   - Select Wallet: Switches the currently selected wallet.
   - Create New Wallet: Click to create a new wallet.
   - Import Wallet: Wallets can be imported via the 'Wallet Seed''Keystore''Extended Public Key''Hardware Wallet'. (A pop-up window prompts the user when importing duplicate wallets.)
   - Backup Current Wallet: Save a backup of your current wallet after verifying your password.
   - Export Extended Public Key: Export the Extended Public Key file.
   - Delete Current Wallet: Delete the current wallet after verifying the password.
2. Edit:
   - Cut: Command/Ctrl+X
   - Copy: Command/Ctrl+C
   - Paste: Command/Ctrl+V
   - Select All: Command/Ctrl+A
3. Tools:
   - Sign/Verify Message
   - Multisig Addresses
   - Clear all synchronized data
   - Offline sign
   - Broadcast transaction
4. Window:
   - Minimize: Command/Ctrl+M
   - Close Window: Command/Ctrl+W
   - Lock Window: Command/Ctrl+L
5. Help:
   - Documentation: Open your browser and jump to the Neuron documentation page.
   - Nervos Website: Open your browser and jump to https://www.nervos.org.
   - Source Code: Open your browser and jump to https://github.com/nervosnetwork/neuron.
   - Report Issue: Open your browser and jump to https://github.com/nervosnetwork/neuron/issues
   - Contact Us:neuron@magickbase.com.
   - Export Debug information: Export the debug information file.
   - Settings: Open the Settings page.
   - Check for Updates: Click to check for updates.
   - About Neuron: Displays the current version and the node version.

### Top status bar
1. Light and dark mode switching: Click to switch the Neuron display mode.
2. Network: Displays the current network environment.
3. Synchronizing Progress: Displays synchronization progress and status.
   - Block synced: Displays the synchronized block height as well as the latest block height.
   - Time Remaining: Displays the remaining time required for synchronization to complete.
   - Start block: Displays the set synchronization start block.
   - Set start block number
   
### Overview
1. Balance: Displays the full current wallet balance and locked balance. (needs to be synchronized to the latest block)
2. Address Book: Click to open the address book.
   - The categories are All, Receiving, and Change, and show All by default.
   - Supports sorting by balance and Txs.
3. Cell Management: Click to open Cell Management.
4. Send&Recive: Click to make an on-chain transaction
5. Recent activities: Display recent transaction history and details

#### Send&Receive
1. Send： Initiate on-chain transactions
   - Send to Adding an address on the CKB chain for transactions
   - Amount: Enter the amount to be sent, optionally click MAX to enter the maximum value automatically.
   - Add an address: Adding additional CKB on-chain addresses for transactions
   - Set lock time: Set the lock time of the transaction, which may be inaccurate due to the uncertainty of the block-out time.
   - Description: Add description to this transaction
   - Transaction Fee: Displays estimated transaction costs based on current transactions and on-chain data.
   - Price: Select the recommended rate or customized rate, the default customized rate supports the selection of slow/standard/fast.
   - Chained Transaction: Allow use of unconfirmed outputs which can reduce transaction fees and increase speed of recognition. (Disabled by default)
   - Submit Transaction: Submits transactions after verifying passwords and provides the ability to export transactions.

2. Send Confirmation Page: Confirm the transaction information and submit.
   - Basic information: Contains 'Amount' 'Transaction fee''Size''Cycles' and 'Lock Time' information.
   - Topology Graph: Displays a topological complement consisting of transaction inputs and outputs.
   - Verify Password: Enter the password and verify it before sending.

3. Receive: Receive on-chain transfers
   - Address QR code： Provides a QR code image of the current address and offers download and copy functions.
   - Address： Displays the receiving address under the current wallet, with the new address selected by default to ensure user privacy and security.
   - Toggle Address Format： Displays the full address by default and provides the ability to switch to a deprecated address format.
   - Hardware wallet: Provides the ability to verify the address when using a hardware wallet (requires connection to the wallet)

#### Cell Management
1. List of live cells: View and manage live cells.
   - Data: Displays the time at which the cells were acquired, in descending order by default. (Support Sorting)
   - Type: Displays cell type, contains 'CKB' 'UDT' 'NFT''Unknown'. (Support Sorting)
   - Amount: Displays the amount of cell assets. (Support Sorting)
   - Status: Categorized as locked and unlocked. (Support Sorting)
   - Description: Users can add descriptions to the cells.
   - Operation: Users can view details, lock/unlock, and consume operations on cells.
     - View details: Pop-up window showing cells 'OutPoint.TxHash''Lock Script''Type Script''Data'and'Capacity Usage'.
     - Lock/Unlock: Supports lock and unlock operations on cells, but only takes effect locally. (Some types of cells are unable to perform lock/unlock operations, such as 'NervosDAO')
     - Consume: Consuming and sending the cell out in its entirety does not retain the data inside the cell.

>To be updated
>### History
>1. Search: Search for Tx hash, address, or date to find the transaction.
>2. Export: Export transaction history in CSV format.
>3. Transaction List
   - Type: Display the type of transaction.
   - Assets: Displays the amount received and spent assets for the current transaction.
   - Balance: Displays the change in balance as a result of this transaction.
   - Time: Displays the date and time of the transaction (accurate to the second)
   - Status: Displays the on-chain status of the transaction.
   - Operation: Expand or collapse the information of the transaction.
   - View Details: Provides the ability to view transaction details in the expanded state and supports opening in an explorer.
>4. Transaction Details
   - Basic Information: Displays the transaction hash, block number, date, and income.
   - Inputs and outputs: Displays the input and output parameters of the transaction.

### Nervous DAO
1. Account Info: Displays the available account balance, locked amount, and current APC.
2. Deposit: Click to initiate a transaction to deposit into the Nervos DAO. （Show rewards when depositing）
3. Deposit and completed list: Displays deposited and completed transactions for Nervos DAO.

### Settings
1. Wallet: Switch the current wallet account.
   - Add one more: Add a new wallet.
   - Detect duplicate wallets: Support for deleting duplicate wallets when they exist.
2. General
   - Version: Displays the current version and offers to check for updates.
   - Language: Select language, currently supports English and Chinese.
   - Keeping screen awake: Off by default, on to keep the screen awake during synchronization.
3. Network: Select the network node used by the wallet.
   - Internal Node: internal Main node. (Unable to modify and delete)
   - Light Client: Light client node with support for switching between main and test networks. (Unable to modify and delete)
  - Customized nodes: External nodes added by the user. (Able to delete and modify)
4. Data: Selects data storage paths for nodes and indexes as well as providing cache cleanup.
   - Set path: Displayed only in full node mode, supports modification of storage paths.
   - Cache: Refresh the cache to resolve synchronization or balance display issues.

### Experimental

#### Customized Assets
1. Synchronization： Full node mode synchronization needs to be completed before all custom assets can be displayed.
2. Customized Asset List
   - Time: Displays the time when the asset was traded and uses this to sort the list (from late to early).
   - Asset: Displays the name of the identified asset and the unidentified displays the unknown asset.
   - Operation: Support claim, transfer, withdraw, and migrate assets as well as check transaction details. (Locked assets and unidentified assets not available for claim)

#### Assets Accounts
1. Search: Search for the account name, token name, or symbol.
2. Create an asset account： Create a sUDT or CKB account to accept customized assets.
3. Account List： Displays the custom asset accounts that have been added.

### Wallet connect

### Dark Mode
Change the theme color of the software by clicking the top icon to switch to dark mode.


### Light Client Mode
Light Client Mode is a connection mode for Neuron that can be realized by connecting to the built-in CKB Light Client node through the network settings in the settings. It downloads a portion of the blockchain data to >get the necessary information compared to a full node. This allows Neuron to access the CKB blockchain faster.





 
