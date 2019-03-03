# Introduction to NEM Blockchain
v.2.3.0

## Topic 1： History of NEM
It answers the questions of:  
● What is NEM?  
● When was NEM started?   
● What next?  

Few years after the introduction of Bitcoin, more people are aware that blockchain is powerful beyond Fintech. Many different blockchains were introduced. On January 19th in 2014, a post in bitcointalk.org introducing the idea of NEM was published.

[**NEM is the New Economy Movement**](https://bitcointalk.org/index.php?topic=422129.0)  
`A groundbreaking crypto-currency that gives control of their economy back to the people and establishes them as sovereigns over their own destiny. A currency is an expression of a political ideology and social attitude. Do not mistake us as just another cryptocurrency. We are more than a cryptocurrency, we are a New Economy Movement.`
  
Interested parties can join with contributing 300 NXT or 0.03 BTC for an equal stake to be shared among contributors. NEM Foundation was later formed when there were certain stakes were not claimed after a year XEMs were mined and distributed.  

The main developers of NEM are Jaguar0625, Gimre and BloodyRookie. They remain active until this very day.  

NEM was coded from ground up in Java, though initially it was planned to fork from NXT. In 29th March 2015, with its first block being created UTC 2015-03-29 00:06:25.000 AD. It has been running since with zero downtime and no major glitch. NEM native currency is XEM, pre-mined with a fixed number of 8,999,999,999 XEM with 6 divisibilities.  

In 2016, Tech Bureau, one of Japan largest cryptocurrency exchanges partnered with NEM to power NEM private blockchain, called Mijin.  

The version 2 of NEM blockchain is developed using C++. It is targeted to be released in 2019 under the code name Catapult. Catapult is open source and comes with extra functions, like aggregate transaction, multi-level multisignature and cross-chain transactions.  

Features in Catapult are plugins. They are customisable to suit the needs of each chain. With the open source, contributions from the community are very much welcomed and setting up of private chains will populate the Catapult ecosystem and present the opportunity of vibrant cross-chain atomic swaps.  

`NEM is initially an acronym for “New Economy Movement”. It is now generally just referred to as NEM.`

## Topic 2： Architecture of NEM
It answers the questions of:  
● How NEM1 works?  
● Where to look for guidelines and instructions?   
● How NEM2 works?   

**NEM1 Architecture**  
NEM is one of the easiest blockchain platform to work on, if not the easiest amongst all. It is API-ready where applications can be integrated with NEM Blockchain as soon as within weeks, depends on how elaborated the applications are intended to integrate with NEM Blockchain.  

NEM1 applies 2-tier architecture. Data stored on the NEM Blockchain can be called while data can be written into NEM Blockchain both through API endpoints. Data is written and readable through JSON object.    

**NEM1 Blockchain:** Persistent layer where the immutable and traceable data will be stored.  
**Application Layer:** This is where your business logic resides. E.g. NEM Wallet.  

Library, SDKs and wrappers are available for the following languages and will be expanded from time to time:   

**Python** (https://github.com/semolex/nis-python-client)  
**Java** (https://github.com/NEMPH/nem-apps-lib)  (https://github.com/rosklyar/nem-library)  
**C#** (https://github.com/NemProject/csharp2nem)  
**Typescript/Javascript** (http://nemlibrary.com)  
**Javascript** (https://github.com/QuantumMechanics/NEM-sdk)  (https://www.npmjs.com/package/nem-api)  
**NodeJS** (https://github.com/NemProject/nodejs2nem)  
**Ruby** (https://github.com/44uk/nis-ruby)  
**PHP** (https://github.com/namuyan/NEM-Api-Library) (https://github.com/tomotomo9696/NEMTools_PHP) (https://github.com/evias/nem-php)  
**Go** (https://github.com/nem-toolchain/nem-toolchain)  

For projects that would like to develop their own APIs, the detailed documentations of NEM Infrastructure Server’s (NIS) APIs is available at https://nemproject.github.io/

**NEM2 Architecture**
NEM2 Catapult applies 4 layers architecture:

`Online: (Internal)`  
1. The blockchain core of peer-to-peer network.  
• The blockchain layer.  
• Where the transactions and verifications happen.  
2. MongoDB and API Server (REST nodes)  
• Transactions being announced through this layer.  

`Offline: (External)`  
3. SDKs  
• Where transaction is being prepared and signed.  
• At the application level.  
4. Light weight clients.  
• Applications.  

## Topic 3: Benefits of Building on NEM
It answers the questions of:  
● Why build on NEM?  
● How secure is NEM?  
● What would be the decision factors to build on NEM?  

**The 5 main reasons to build on NEM**
1. Security
The mechanisms that keep NEM Blockchain well-guarded are stated below.  

[*I. EigenTrust++*](https://nem.io/wp-content/themes/nem/files/NEM_techRef.pdf)

It is a node to node reputation mechanism. This algorithm helps in identifying bad actor in the network. It also helps the node to select their communication partners according to the trust values of other nodes.  

While interacting with each other, nodes share information. The information will be seen as either a success, neutral or failure. Each node then keeps track of the outcome of all its interactions with other nodes by counting successful and failed interactions. Neutral interactions are ignored.  

*II. Proof-of-Importance (POI)*
`[Chapter 7 of technical paper](https://nem.io/wp-content/themes/nem/files/NEM_techRef.pdf)`
NEM introduced its own consensus protocol called Proof-of-Importance. With higher importance score, an account will have higher chance to harvest a block and be rewarded with transaction fees that come with the harvested block.  

PoI score will be initiated once an account has 10,000 vested XEM. To calculate the importance of an account, 3 factors are considered:  

- **Vested amount**  
*For every 1440 blocks, about 24 hours, 10% of the unvested xem in an account will be vested. Once the vested amount has reached 10,000 xem, the account is eligible for importance calculation. In order to reach 10,000 vested xem, you will need more than 10,000 xem in the account. Else, it will never reach 10,000 vested xem. The more xem an account has, the faster it will reach 10,000 vested xem.*   

`[All accounts in the nemesis block are fully vested.](https://nem.io/wp-content/themes/nem/files/NEM_techRef.pdf)`

- **Number and size of transactions** for the past 43,200 blocks (about 30 days). The number of transactions an account made and the size of the transactions matter for the importance calculation. The more transactions an account made, and the higher the amount in a transaction, the higher the importance score. Only transaction with over 1,000 xem and more are eligible for the importance calculation, and the transaction needs to be sent to another account with 10,000 vest xem. [link](https://blog.nem.io/how-do-i-get-importance-on-the-nem-blockchain/)

In addition, transactions that were made a day ago play a more important role than those were made 20 days ago.

- **Transaction partners**
It also important with whom it made the transactions with. Accounts that try to send xem back and forth between each other will not gain importance as only net transfer is counted over the period of 30 days. NCDaware Rank, similar to Google PageRank, is used to calculate salience of a node in the network.  

PoI rewards users rather than hodlers. It promotes varieties of use cases rather than just fintech.

`When an outgoing-transaction is being made, the total amount of xem will be coming from both vested and unvested amount.`

`The process of including a block in the NEM Blockchain is called “harvesting”.`

*III. Spam Protection for Unconfirmed Transaction*  

Bad actors take advantage of low transaction fees to flood the network with new transactions in order to disturb the network. To minimize the risk, the nodes need to limit the number of unconfirmed transactions handled by nodes. However, this might limit good actors at the same time, and the bad actors can create as many accounts at the same time.
   
NEM has a custom spam filter that decides if an unconfirmed transaction should be processed or rejected.

- Consider the unconfirmed transaction cache as having 1200 slots for normal transactions and another 1200 slots for multisig transactions, as long as there are less than 120 transactions, all transactions will be processed.
- Otherwise, a fair share of slots for the new transactions will be calculated. If the new transaction occupies less slots than its fair share, it will be accepted. Refer to page 14 of [Technical Referene](https://nem.io/wp-content/themes/nem/files/NEM_techRef.pdf)
     
`When a new transaction is created and broadcasted to a node, it will be put into the pool of unconfirmed transaction cache, and be broadcasted to other nodes if it is valid.`

`During the block chain synchronization round, there is a poll mechanism for unconfirmed transactions which allows nodes which do not have their port 7890 open to still be able to learn about new unconfirmed transactions.`

2. Scalability (Performance and Deep customization)   

Scalability can be discussed in a few angles:  
a) NEM network capabilities  
b) Business logic scalabilities  
c) Customizable  

**NEM Architecture**
NEM applies 2-tier architecture, business logic does not reside in NEM Blockchain. Only data within the transactions will be made immutable and transparent, and be broadcasted to the NEM Blockchain network. This 2-tier architecture has its advantages:  
• As the business logic does not reside in NEM Blockchain network, running a node does not need a very high specifications of hardware since there is not a need to deploy a virtual machine on-chain to run the business logic.
• Fixing bugs, and upgrade of business logics is possible as it is not deployed on chain.
• Transaction fees is cheaper as the business logic is run off-chain and only the end result is stored on NEM Blockchain. Hence, there is not a need for high transaction per second.

`There are debates about low transaction per second (tps) in NEM, which is 2 tps. It is a soft-cap. It is scalable to higher tps however it comes with the price of hardware upgrade of nodes. In addition, while most of the transactions and calculation in business logic to be done off-chain, less transactions are needed to be on-chain. Currently, NEM has not hit full block, hence, there is still much room to grow with current tps.`
               
**Mijin – Private Chain**  
The private chain, Mijin, which is using Proof-of-Stake (PoS) is scalable to 1000 tps and more if such a high transaction volume is needed.  

**NEM Smart Asset System**
NEM1 has 5 built-in on-chain features, namely `Account, Namespace, Mosaics, Message and Multisig`. NEM2, Catapult, has additional 3 features, which are `aggregate transaction, multi-level multisignature and cross-chain swaps`. With these features, you can create your customised smart assets.  

3. Speed (Ease of development)  
As NEM is API-driven and SDKs, library and wrappers are available for different languages, integration with NEM Blockchain will take much shorter time due to:  

- Enterprises do not need to re-write the applications they are using. Their current system can be integrated to NEM Blockchain through API. Retooling of existing infrastructure is not necessary.  
- Not necessary to train users about new applications.  

4. Stability  
Since the Nemesis block was created on 29th March 2015, NEM Blockchain has not have any major security issue. Being a blockchain that was coded ground up also means that it does not inherit the flaws of the blockchain it forks from. The following few factors contributed to its stability.  

-  [P2P Time Synchronization](https://blog.nem.io/first-ever-p2p-time-sync-for-nodes/)  
Through a custom protocol, NEM Blockchain avoids valid transactions and blocks being rejected due to the different timestamps each node has. Time sync for NEM does not rely on node outside of the network.  

In NEM Blockchain network, each node manages an integer number called offset which is set to 0 at start. The local system time incremented by the offset, which can be negative, is the network time of the node, in milliseconds. (https://nem.io/wp-content/themes/nem/files/NEM_techRef.pdf)  

The local node will partner with maximum of 20 nodes in the network to perform a time synchronization round. During this process, there could be bad samples due to:  
● Malicious node supplying incorrect timestamps.  
● An honest node that does not know its time is not synchronized.  
● Channel asymmetry. The round-trip time of fetching timestamps from partner node is highly asymmetric due to internet problems or the node being very busy.    

In these instances, filters will be applied to remove the bad samples. There are 3 steps to remove bad samples:  
• If the response from a partner is not received within an expected timeframe.  
• If the calculated offset is not within certain bounds.  
• Alpha trim both ends of the remaining samples in offset ordering.    

The effective offset will then be calculated based few factors, including the importance of the boot account of the node reporting the offset, and multiplied with a scaling factor.  

`Detailed information and calculation of time synchronization is available [here](https://blog.nem.io/first-ever-p2p-time-sync-for-nodes/)`  

If the absolute value of calculated final offset is above given threshold (currently set to 75ms)will be added to the internal offset. This prevent slow drifts of the network time due to communication between nodes having channel asymmetry.  

5. Savings  
a) As NEM integration can be made possible with any language through APIs, no expensive developer for special programming language, e.g. Solidity.  
b) Fast deployment saves time. And time is money. E.g. tokens/coins can be created within minutes with the click of few buttons for NEM.  
c) Cheaper to run NIS than mining machines. NIS does not need special machine to run.  

## Topic 4 NEM Smart Asset System  
It answers the questions of:  
● What’s the NEM 8 features?  
● How to create smart asset?  

The 5+3 features of NEM:  
NEM was initially started with 5 features. Account, Namespace and Mosaic are assets in NEM. With the properties that can be configured and functions that can be called, the assets are customisable to reflect the uniqueness of each asset.  

1. Account  
● An account has a key pair (private and public keys) and an address. Private key is a random 256-bits hexadecimal string with ed25519 elliptic curve cryptography, and public key is derived from private key. Address, derived from public key, is base-32 encoded and 40-character long, consists of network byte, 160-bit hash of the account’s public key and 4-byte checksum.  
● Acts as a container for information about an asset that needs to be unique and updateable. e.g. It is a holder of XEM.  
● It can be assigned to represent anything.  
● Every account is unique and non-duplicable.  
● An account can be owned by a single owner or owned by several other accounts, i.e. multisig account.  
● While transactions made to blockchain are immutable, the status of an account (Account State) can be updated. Historical trail of an asset can be traced using account. Account state consists of:  
○ account balance.  
○ number of harvested blocks.  
○ height of the first transaction that referenced the account  
○ list of multisig accounts and list of co-signatories.  
○ information about delegated account status.  
○ importance and NCDawareRank.  
○ vested balance.  
         
`When generating a new account using NEM Wallet, the public key will not be shown. It will be available when a transaction is made or made to the account, as the account generated in NEM Wallet is generated offline. Account generated using API is generated online and will have the key pair and address right away.`
           
2. Namespace  
● Namespace is owns by an account.  
● Similar to domain name for internet.  
● Up to 3 levels: root namespace, sub-namespace level 1, sub-namespace level 2. E.g. Universe.Earth.Asia  
● Root namespace needs to be unique within NEM blockchain. Sub-namespace needs to be unique within its own level. A root namespace can have a maximum 16-characters, and 64 characters for sub-namespace.  
● Naming of namespace and sub-namespace can start with lowercase and uppercase of alphabets, and numbers. Underscore and hyphen can be used only within the names.  
● Rental of namespace is 100 xem and 10 xem for sub-namespace. The rental last for a year. Renewal can be made 30 days before expiry with another 30 days of grace period. Sub-namespace and mosaics will become obsolete if root namespace is not renewed.  
● Root namespace is a must before creating mosaic.   

3. Mosaics  
● Fungible. Represent fixed assets that do not need to have unique identification.  
● It represents identical things that do not change.  
● XEM is the native mosaics of NEM. It is held within accounts (addresses) and can be passed within accounts and change the status of the accounts.  
● Mosaic ID maximum length is 32 characters. It can start with lowercase and uppercase of alphabets, and numbers. Underscore and hyphen can be used only within the names.  
● Fee for creating a mosaic is a one-time fee of 10 xem.  
● Mosaic is concatenated with namespace with a ‘:’. E.g. Universe.Earth.Asia:Malaysia.  
● Description of mosaic may not exceed the length of 512 characters. It can be altered, however, each alteration will cost 10 xem. Take note that this is valid only if all the coins created is recalled back to the creator’s account. The same “mosaic definition creation transaction” that is used for creating mosaic is used for changing the definition of the mosaic.  
● Properties of mosaic:  
○ Maximum supply: 9 billions  
○ Divisibility: maximum 6  
■ This feature is powerful especially when the amount of the asset the mosaic is assigned to represent is more than 9 billions in number.  
○ Transferability: true or false  
■ When it is set to false, the mosaic can only be transferred from the creator and to the creator.  
○ Mutability: true or false  
■ When set to false, the total supply of the mosaic cannot be changed.  
● Transaction fees of mosaic are always be paid in xem. Extra fee may be collected through imposing levy. The following information need to be specified for levy collection:  
○ Fee type: Levy can be of an absolute fee or percentile fee.  
○ An address of a recipient needs to be specified. Usually it will be an account belong to the entity setting up the project.  
○ MosaicID for the mosaic that will be used to pay the levy.  

4. Messaging  
● Message can be attached to a transaction, either unencrypted, encrypted or in hexadecimal form.  
● Maximum size of the message is 1024 bytes. For encrypted messages, 49 bytes are reserved for encryption purposes.  
● Through messages, invoice number, serial number and even a whole book in hashing format can be attached.  

5. Multisignature (multisig)  
● NEM1 natively supports m of n multisignature account, where m is the number of the co-signatory need to sign in order to complete a transaction. n is the total number of co-signatory the said account has.  
● Through an aggregate modification transaction, an account can be turned into multisig account. After the change of the status, the multisig account can no longer initiate a transaction. A transaction by multisig account can only be initiated by one of the co-signatories.  
● A few cosignatories can be added in one transaction, however, only one cosignatory can be deleted in a transaction.  
● It is useful for corporate accounts where multiple signatories are required to approve a transaction.  
● It can have maximum 32 cosignatories. The greater the n, the more expensive it is to convert from unisig to multisig account. The greater the m, the more expensive it is to have a signed transaction.  
● The multisig account is safer than a single signatory account. This is because an attacker will not be able to initiate a transaction even if the attacker gains access to the private key of the multisig account, or even to the private key of one of the co-signing accounts.  

`In m of n, m always has a number smaller or equal to n. When m=n, to delete a signatory, n-1 is applied.`
     

*Caution:*  
● Please ensure the account to be converted into multisig account as enough xem for the transaction.  
● The account to be assigned as cosignatory need to have past confirmed transaction so that the public key is published in the blockchain.  
● If for instance all private keys of the co-signatories of a multisig account reside on a single computer then the multisig account is essentially as good as a normal account because if that computer gets compromised, all private keys are disclosed to the attacks at once. (https://nemproject.github.io/)  

The next 3 features are only available in NEM2, Catapult.  

6. Multi-Level Multisignature  
• Works similar to Multisignature account. Enhanced with multi-level features.  
• Using same plugin for multisignature.  

7. Aggregate Transactions
• Merges multiple transactions into a onetime disposable self-executable algorithm that allowed trustless transactions.
• All transactions will be executed at the same time once all participated parties have signed.  

There are 2 types of aggregate transactions:  
- a) Aggregate complete  
o There is only one signing account for the transactions. i.e. transactions from one account to many accounts.  
o The signing account need to sign the aggregate transaction once rather than signing multiple transactions.  
o Whenallrequiredco-signatories(formultisigaccount)havesigned the transaction, the aggregate transaction is considered complete. o All the inner transactions will be executed at the same time, provided there is no validation error, e.g. not having enough mosaics for any of the transactions.  
o All types of transactions can be included in one aggregate complete transaction.  

- b) Aggregate bonded  
o There is more than one signing account.  
o A Lock Funds Transaction confirmation is needed for announcement of aggregate bonded transaction. This is to prevent network spamming.  
o Lock funds will be harvested if any of the involving parties fail to sign the transaction within the time limit.  
o Lock funds will be returned if the transaction is successful.  
o Lock funds will be harvested if the transactions fail.  
o An aggregate bonded transaction will be in partial status once it has been announced and still pending for all involving parties to sign. Once all involving parties have signed, the status will change to “unconfirmed” waiting to be included in a block.  

8.[Cross-Chain Swaps](https://nemtech.github.io/concepts/aggregate-transaction.html#)  
• Enables tokens trading across different blockchains (between Catapult public and private chains that have common framework and protocol) without using intermediary, e.g. an exchange service, in a trustless environment.  
• Senders of transactions will need to provide a secret lock where the receiver need to provide a proof in order to receive the transaction.  
• Even if one party fail to proof for the transaction, another party can still claim the transaction as long as the proof of the transaction is being presented.  
• After the proof being presented, it will depend on each chain for the confirmation of transaction.  
• However, no other account can hijack the transaction by presenting the proof, though anyone can present the proof, the transaction will still be sent to the designated account address.  
• There are 2 important properties for cross-chain swaps:   
o Secret proof transaction.  
▪ Generate a proof randomly.  
▪ The secret proof is used to unlock the secret lock.  
o Secret lock transaction.  
▪ Generate secret lock through hashing the secret proof with one of the available 4 algorithms. Both chains need to adopt the same algorithm.  
• SHA_3    
• Keccak    
• Hash_160     
• Hash_256    
▪ Define the amount of mosaics to be transferred. Which these mosaics will be lock by the secret lock until the secret proof is presented. This is to ensure there will be fund available for the transaction.  
▪ Define the lock duration.  
▪ Announce the transaction.  
▪ If the secret proof is failed to be presented, the locked mosaics will be unlocked and returned to the initiator when
the duration is reached.  

Example:
• Alice generates the secret proof hash and secret lock hash and announce the secret lock (TX1) in the “Private Chain”. The “Private Chain” will lock the mosaics amount defined by Alice.  
• There will be an incoming transaction for Bob’s account in “Private Chain”.  
• On the “Public Chain”, Bob will generate another transaction with the secret hash he gets from TX1 from “Private Chain” and announce it (TX2) in “Public Chain”. Alice account in “Public Chain” will now has an incoming transaction.  
• Alice will then present the secret proof transaction to claim the TX2 on “Public Chain”. The transactions will then be executed and wait for confirmation from “Public Chain”.  
• With the same secret proof transaction presented to “Private Chain”, TX1 in “Private Chain” will be executed and wait for confirmation.  
• The transactions are considered concluded:  
- I. When both the secret locks transactions are unlocked, and the funds are being reverted to respective accounts.  
- II. When the secret lock duration is reached, if any of the secret lock transaction is not being unlocked, the locked amounts will then be rolled back to the transaction initiators if not claimed.  

### References
● (https://nem.io)  
● (https://blockchainhub.net/blockchains-and-distributed-ledger-technologies-in-general/)  
● (https://en.wikipedia.org/wiki/List_of_cryptocurrencies)  
● (https://bitcointalk.org)  
● (https://docs.nem.io/)  
● (https://nemproject.github.io/)  
● (https://blog.nem.io/)  
● (https://nem.io/wp-content/themes/nem/files/NEM_techRef.pd)  
● (https://www.reddit.com)  
● (https://nodeexplorer.com/index)  
● (http://explorer.nemchina.com/)  
