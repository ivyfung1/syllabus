#APPLYING NEM

## Topic 1: Do you need Blockchain or Not?
**Is Blockchain necessary?**
Everything can be blockchained, however, not everything needs to be blockchained. Ultimately, Blockchain is here to solve the `TRUST `issues through:  
• Immutability  
• Traceability  
• Transparency  
• Decentralization  

As the NEM Blockchain has the business processes being stored off-chain, then the question would be what is being stored on-chain?   The data should be:  
• The outcome of the process.  
• The value being transferred.  
• The parties/stakeholders involved in the process.  
• Information that would need to be made immutable.  
`In general, Blockchain is a log of values changing hands.`  

## Topic 2: Non-Fungible Assets    
Creating non-fungible assets is one of the important features for Blockchain. A non-fungible asset would have the following features:  
● It is not interchangeable. For example, token A is not equal to token B. Cryptocurrencies are fungible as no matter which XEM I own, it always denotes the same value.  
● It is unique on its own as there is no duplication of it. Non-fungible assets are used to create verifiable digital scarcity. They are used in crypto-collectible or crypto-gaming and it can also be used for proving authenticity and ownership. This gained popularity because the use of ERC-721 token for Crypotokitties.  

**Non-fungible assets in NEM**  
One may try to use Mosaics to create non-fungible assets. A Mosaic is flat by nature so it is fungible. For this reason, out of the 5 features, an account will be the best choice for a non-fungible asset as every account is uniquely defined by its address. The characteristics of an asset can then be denoted by the mosaics stored in it.  

*Use case scenario example*
`A dog trainer game.`
Every dog is represented by an account. For every trick it learns, a special mosaic will be added to the account representing it. For example, a mosaic for rescuing people, a mosaic for climbing tree, a mosaic for swimming etc. The more types of mosaics the account has will denote that the dog has learned certain tricks. The greater number of same mosaics in the account will denote the level of skills the dog has.
       
## Topic 3: Escrow Services
Escrow refers to money held by a trusted third party on behalf of the transacting parties while each of them fulfill the terms and requirements stipulated. Escrow services are common in real estate transaction, e-commerce, a judicial context, merger and acquisition etc.  

**Escrow function in NEM**
For NEM, all possibilities happen with the combination of the 5 features. Escrow means to have a third party to act as a moderator. Through its multisignature feature, where the moderator is assigned as one of the cosignatories of the multisig account, an escrow service can be established.  

First, an account has to be created and then turned into a multisig account adding the transacting parties and the third party as the cosignatories (i.e. there needs to be at least 3 signatories for the multisig account). The account is meaningful only if 2 out of 3 parties are to sign. If it only requires one of the three to sign, it defeats the purpose of having a trusted party. This is because as any of the transacting parties would be able to withdraw the token from the multisig account or transfer its ownership through deleting the other cosignatories and adding new signatories.  

*Use case scenario example*
Using the non-fungible dog training case study above, transferring the ownership of the trained dog is tricky as it is the account that is non-fungible, not the mosaics. Hence, transferring the ownership of the trained dog would need to involve the multisig account feature.  

The account that represents the trained dog first needs to be turned into a multisig account having the seller, the buyer and the gaming company as cosignatories with 2 out of 3 required to sign. After the payment is done by the buyer, the seller and the gaming company can delete the seller from the multisig account, with the gaming company subsequently being deleted from the multisig account as well.

Though, the private key of the account representing the trained dog is known by the seller, however, as the private key of a multisig account is only used to sign transaction, the account is considered safe, if it remains a 1 of 1 multisig account.

`Escrow can be achieved with Aggregate bonded transaction in Catapult too.`
    
## Topic 4: Storage on Blockchain
It answers the question of:
● What is the best way to store data on-chain?
● What data to be stored?
 
Why choose blockchain over conventional databases?  
1. The decentralization of data as there is no administrator who can manipulate the data in the server.  
2. Each transaction made to the blockchain is a log by itself.  
3. It is more secure and dependable as the data is immutable governed by all nodes in the network.  
4. With decentralization comes transparency as the transactions are transparent to all. Encryption becomes important if the data is to be kept confidential.  

**Storing or transferring data in NEM**  
There are few ways to store data on a blockchain:  
1. Saving data through transaction.  
Every transaction contains some data, e.g. the sender, the recipient, the amount, and the message.  
2. Sending data through messages.  
The message field in NEM transactions provide options for data storage, with a limitation of 1024 characters in bytes before encryption. Here are examples of what can be stored in the message field:  
• Invoices number, purchase order number etc.  
• Serial number.  
• Programming parameters, JSON, raw data etc.  
• Data in hexadecimal form

*Use case scenario example*
The message field of the transaction can be used to store an invoice number of a done deal, or to store the hash of a document for notarization purposes.
                              
## Topic 5: Exchange and Wallet

Most mosaics are targeted to be tradeable in an exchange. For an exchange to list a mosaic, it must be able to receive the mosaic that is being sent to. There are few ways of designing a wallet for an exchange in order to receive mosaics.  

Please refer to "[Exchange Support](https://github.com/st-wong/NEMExchangeSupport)" prepared by Shin Tatt.

## Topic 6: Tokenized Assets

There are 2 categories of tokens:
1. `Utility Token`: It allows the owner of the utility tokens to use the services provided by the project/application.    
2. `Security Token`: It is assets-backed. Each token represents an asset or a portion of the asset. It can represent properties, machines, furniture, factory productions etc. In fact, it can represent practically anything.
Anything can be tokenized, however, not everything needs to be tokenized. The following are good reasons for tokenizing assets:  
• To allow ownership of a fraction of an asset.  
• To keep track of the transfer of ownership of an asset.  
• For supply chain purposes.  

*Use case scenario example*
Create a mosaic with 9 billion initial supply with a divisibility of 6 to track up to 9 trillion units of slippers being manufactured.  

Or, create a mosaic with 100 initial supply to represent a percentage of a property. The number of mosaics own by a certain person represent the percentage of the property that a person owns.        

## Topic 7: Supply Chain

Refer to https://nemtech.github.io/nem2-workshop-nem-applied-to-supply-chain/lessons/use-case/ The case mentioned  involved multi-level multisignature features by NEM2, Catapult.  
    