# Blockchain

# Topics
1. Features of Blockchain  
2. The Technology behind Blockchain  
3. History of Blockchain  
4. The future of Blockchain and Its Use Cases  

## Topic 1: Features of Blockchain  
This topic answers the questions:  
• What is Blockchain  
• What are the characteristics of Blockchain?  
• What can Blockchain do?  

**Define Blockchain**
`Blockchain is to Bitcoin, what the internet is to email.`  
When we discuss the topic about Blockchain, we will inevitably bring up the topic of Bitcoin. This is unavoidable as it is the hype of Bitcoin that has brought the world’s attention to the technology behind it, which is Blockchain. However, Blockchain is not just limited to Bitcoin.   

What is Blockchain? Blockchain is a set of digital ledgers, called blocks, recorded with transactions or facts and being published for the community to view. Those blocks are chained chronologically with digital signatures, hence the name `BLOCKCHAIN`.  

What are the main features of Blockchain?  

1. Distributed Network
**Centralized:** There is a server and clients are connected to it, with data being sent to and fro between the server and the clients. The server would be the single point of failure. If the server fails, everything else fails. Data manipulation is possible and easy.  

**Decentralized:** There is more than one server connected to each other and clients are connected to one of the servers. There are also more than one points of failure, hence, it is less vulnerable. If one server fails, there will be other servers. Continuity and recovery are highly possible. Data manipulation, although more difficult, is still possible.  

**Distributed:** There are no servers or clients. Each computer (node) is connected to each other. When data is distributed amongst the nodes, as long as one node is still running, recovery and continuity is still possible. There is no one or few points of failure making it very difficult to shut down a system. At the same time, forgery and manipulation of data is near impossible as the manipulation needs the majority of the nodes, and the number of nodes can be continuously increased.  

2. Secured
The hash function and cryptography play important roles in Blockchain technology. They give blockchain multi-layer security systems.  

Hash function is a mathematical function. Its output can be referred to as a type of digital fingerprint or digital signature. 

In addition to the hash function, each transaction generated for the blockchain needs to be signed with the private key of the account initiating the transaction. The signed transaction is then announced to be included in a block.

It is VERY important to keep the private key safe or even offline, as the person who has access to the private key will have access to the properties of that account.  

3. Immutable
Having blocks (distributed ledger) being chained together chronologically means it will leave a historical trail. You can always trace the transaction back to its origin, which is the first block created, also called the Genesis Block. All transactions, or facts, being recorded in the blocks are time-stamped with the network time. All blocks are linked to each other one after another through a hash function.  

In order to change any data blocks before the current one, you need to regenerate the digital signature of the block you want to alter and also the digital signatures of other blocks immediately following it. This is because as each block contains the digital signature of the block immediately before it. Each block will only have one block immediately before it and only one block immediately after it.  

In order for a block to attach itself to a chain, it will need to go through a consensus protocol where it gets accepted by the majority. Hence, to temper or to commit fraud to a distributed ledger, you will need to have they majority says, which is 51%. To achieve 51%, it needs a huge financial commitment in most cases.  

4. Transparent yet anonymous  
Blockchain is made up of public ledgers that are connected to one another with all the transactions inside the ledger clearly stated. The sender, the receiver, the amount of tokens involved, and any information that the sender wants to include in the transaction, all are publicly available to be scrutinized, be it encrypted or not. This transparency allows the tracking of funds and properties from the very beginning until the current stage.  

With high level of transparency, the benefits are as below:  
• Easily auditable ledgers/transactions that cut down on auditing time. This is especially so in financial world where auditing and reporting costs are high.  
• The tracing of a particular transaction is fast. Each of the account in the blockchain is represented by an address. Even though all transaction information is transparent in the eyes of the public, the identity of the account owners (a.k.a. the senders and the receivers) will be identified as nothing but a string of characters, which is the address. Unless the owners of the addresses publicly announce their ownership, they will remain anonymous.  

5. Fast and economical
Being distributed, a blockchain is operating in a trustless environment. There is no need for a trustee, which also means there are no intermediaries needed. Let’s take a look at traditional financial industry as an example. In order to make a transfer to someone in another country, we have to go through financial institutions as the intermediaries, and the clearance may take days, with high fees incurred.  

In Blockchain however, funds can be transferred within seconds and confirmation can be a matter of minutes. This has reduced the timespan and cost of a transaction.  
    
`Higher transaction fee for priority inclusion in block.`  

## Topic 2: The Technology of Blockchain

This topic answers the questions:  
• What issues can Blockchain solve?  
• How does Blockchain work?  
• What is not Blockchain-related?  

**What issue are Blockchain trying to solve?**
`TRUST` is the main issue blockchain tries to solve. Often during business dealings, 2 parties do not trust each other and need a 3rd party as an intermediary. Blockchain’s peer-to-peer network takes away the intermediary. (E.g. transfer of monetary value without bank.) The following characteristics of Blockchain solve the TRUST issue:  

• Transparency: All the transactions are transparent in Blockchain. As such, there is a historical trail for the transactions done.  
• Traceability: With a historical trail, a product origin is more trustworthy to the buyer.   (E.g. the origin of a luxury watch and how many previous owners it had).  
• Immutability: Transparency enables traceability and enhance its immutability as any changes of the data will be scrutinised.  

**How does Blockchain works?**  
Let’s go through step-by-step on how a block is created and added to the a Blockchain.  

1. First of all, a transaction needs to be created, broadcasted to the blockchain network and added to a pool of unconfirmed transactions.

2. Miners, also referred to as nodes, on the blockchain network will select the transactions and add them to their candidate blocks. Each transaction needs to pay a transaction fee. Transactions with higher fees will have priority to be added to a block.  

3. The nodes will then go through some algorithm to add their blocks to the chain. Each blockchain adopts a different algorithm, referred to as the consensus protocol. This algorithm is to achieve an agreement amongst the majority. In order for the community (nodes) to be willing to spend their time going through these algorithms, they are incentivized. The few common consensus protocols are:  

a. *Proof of Work (PoW)*
The idea of PoW was introduced in 1993 and the word “Proof of Work” was coined in 1999 (Some said is 1997). It is actually an idea that started in the last century and became popular early this century.   

In blockchain, nodes participating in the PoW will start solving an equation/puzzle. Once a node solves the equation/puzzle, it will add its block to the honest chain and will be rewarded with the transaction fees from the transactions in the block. Some blockchains will reward the successful node with newly minted coins too (e.g. Bitcoin).  

The difficulties of the equation/puzzle will be adjusted automatically and the cost of solving the equation/puzzle is made expensive to discourage fraud. The cost of PoW is in terms of hardware, energy and time. The purpose of PoW is to slow down the process of adding blocks to the chain, so that malicious block can be detected and acted on. Nodes with better computing power will have higher chance to mine a block.  

Aside from the computation work that needs to be done in order for the block to be added to the chain, it needs to obtain consensus from more than 50% of the nodes that it has not been tampered with. PoW is however, vulnerable to 51% majority attack, especially if the number of miners are reduced, as the 51% majority will be easier to achieve with a smaller pool of miners.
Nodes that participate in this PoW are called miners, and the process is called mining.   

b. *Proof of Stake (PoS)*
In PoS, the chance of having a block included to the chain depends on the percentage of stake it holds. For example, if A has 24% of the stake, it has a 24% chance to include its block to the chain and be rewarded. One of the shortcomings PoS has is the “rich man gets richer” syndrome.
Also, using PoS, it is more energy efficient than PoW. The node that is chosen to validate the transactions are called “validator”, and the process is called forging or minting.  

c. *Proof of Importance (PoI)*
Proof of Importance is a consensus algorithm that has been introduced by NEM. The algorithm uses much less energy as compare to PoW.  

As the coin native to NEM, called XEM, are pre-mined, the process of creating a block is called harvesting rather than mining. An account will be allowed to create a block and reap the transaction fees of the transactions being included in said block if certain criteria are fulfilled. Only accounts with importance scores greater than zero are eligible to harvest. To have an importance score greater than zero, an account needs to have at least 10,000 vested XEM. Every day, a 10% of total XEM an account has will be vested, automatically.  

To have higher importance score, the following points matters:  
i. Make transaction with more than 1,000 XEM. Transaction with less than 1,000 XEM will not affect the importance score.  
ii. The amount of transactions in the history of that account with the most recent transactions carry more weight.  

The more active the account in transacting, the more importance score it will gain. This is especially important in a business environment where users are preferred over hoarders.  

4. The node that solves the algorithm will add its block to the chain if the majority of the nodes checks the validity and agrees to it (Consensus). The chain that the block is to be added to needs to be the longest chain (honest chain). The transactions that are included in the block are now considered confirmed. If a transaction is being added in block #100 and the current block number is #105, it means that there are 4 more blocks behind it and the transaction in block #100 has been confirmed 5 times. The more times the transactions are being confirmed, the more difficult it is for an attacker to commit fraud.  

**Topic 3: History of Blockchain**
This topic answers the questions:  

• When did Blockchain started?  
• How has Blockchain becomes what it is today?

Blockchain is not only applicable in the exchange of money but there is no doubt that one of the main functions of the Blockchain is for the exchange of value.  

Bitcoin however was not the first cryptocurrency, nor was it popular right after its introduction. It was only in 2017 that it gained popularity.

1. Pre-Bitcoin
Bitcoin is not the first digital cash/asset. 4 major electronic cash that is worth mentioning prior to Bitcoin’s include:  

a. DigiCash    
1990, David Chaum introduced DigiCash which was the first electronic money offering anonymity of users using a cryptography protocol called Blind Signatures. A bank was still involved in the case for DigiCash. In 1998, it filed for bankruptcy and sold in 2002.    

b. Hashcash  
1997, Adam Back introduced Hashcash. It used PoW to generate new coins. It was designed to filter email spam and DDoS attacks. Its algorithm now forms the basis of mining algorithm.  

c. Bit Gold  
1998, Nick Szabo introduced Bit Gold which also used PoW similar to Bitcoin’s protocol. 

d. B-Money
1998, Wei Dai created B-Money, an “anonymous, distributed electronic cash system” that used PoW and PoS protocol. 

2. Bitcoin
On 18th August 2008, bitcoin.org was first registered, and later that year on 31st October, the whitepaper authored by Satoshi Nakamoto titled “Bitcoin: A Peer-to- Peer Electronic Cash System” was published on the Cypherpunk mailing list. On 3rd January the following year, Satoshi Nakamoto mined the genesis block for Bitcoin.  

The first Bitcoin transaction was 10 Bitcoins on 12th January 2009 from Satoshi Nakamoto to Hal Finney after Finney downloaded the Bitcoin software. Before 2010, Bitcoin basically was worth nothing.   
  
In 22nd May, Laszlo Henyecz offered to buy 2 pizzas with 10,000 BTC. A British national took the offer and ordered 2 pizzas to be delivered to Henyecz. In turns he was reimbursed by Henyecz. This was the first real-world transaction of Bitcoin. 22nd May till today is remembered as Bitcoin Pizza Day.  

In 2011, Bitcoin established parity with US dollar.   
2014, Mt Gox attack. (744,000 BTC stolen).  
September 2016, about 120,000 BTC stolen from Bitfinex.  

1st August 2017, the Bitcoin Cash Hardfork took place where the Bitcoin Cash chain with 8mb blocksize forked from Bitcoin chain with 1mb blocksize.  

2017, the price of Bitcoin hiked from USD963.66 to USD12,952.20 with an all-time- high of USD19,758.20 on 17th December 2017, according to coinmarketcap.com. In March 2017, projects related to Bitcoin in Github passed 10,000. 

3. AltCoins
Any coin aside from Bitcoin are generally referred to as altcoins. One of the popular altcoin is Ethereum. There are other altcoins that came before Ethereum, like Namecoin and Litecoin in 2011,Peercoin in 2013, and Dogecoin in 2014. 

Ethereum was proposed by Vitalik Buterin in late 2013 and was released on 30th July 2015. Like Bitcoin that operates on the Bitcoin Blockchain, Ether (the Ethereum coin) operates on the Ethereum Blockchain. Other coins that operate on Ethereum Blockchain bear the generic name of ERC-20 tokens.  

NEM started on 29th March 2015. It uses the proof-of-importance algorithm and there has not been any downtime since its first block, the Nemesis Block. XEM is the native token operating on the NEM Blockchain. There are also many coins that operate on NEM Blockchain, the famous ones are ProximaX (XPX) and Loyal Coin (LYL). The private blockchain version of NEM is called Mijin.
Other notable blockchains include Hyperledger, NEO, Stellar, ICON, Cardano, Dash etc.

## Topic 4: The future of Blockchain and Its Use Cases
This topic answers the questions:
• What is the future of blockchain technology?
• How will it change our lives?
• How will it impact us?

**The future of Blockchains**
Blockchain technology is only a decade old and is considered to still be at its infancy stages. Blockchains started mainly to cater for financial applications, which is why people often relate blockchain to Fintech. That is not altogether wrong. Fintech is only one of the use cases for blockchain, though it is not the only one.

**How blockchain changes our lives**
Other possible use cases and industries that might face great impact due to the rise of Blockchain technology include:

• Banking and payments (Fintech) 
• Data storage
• Logistics
• Supply chain
• Voting
• Networking
• Insurance
• Healthcare
• Loyalty
• Real Estate
• Crowd Funding