# NEM TECHNICAL

## Topic 1: Types of transactions for NEM1  
It answers the questions of:   
● How to run a NIS1 node?  
● How to communicate with NEM Blockchain?  
● How to request information from NEM Blockchain?   
● How to monitor NEM Blockchain?  

NEM Blockchain network is made up of nodes called `NEM Infrastructure Server (NIS)`. A few facts about NIS:  

● Nodes engaged in a 2-part handshake in order to prevent impersonation-based attacks.  
● NIS is not connected to the network when launched until it is being booted by supplying a private key of a NEM account or assigning a delegated account. The NIS will only able to use GET methods before being trusted by other nodes in the network.  
● A node become more aware of other nodes in the network through announcing transaction and through a refresh.  

**Setting up NIS**  
1. [Download NIS STANDALONE package](https://nem.io/downloads/). As NEM’s consensus is PoI, which has a much lower requirement for computing power, the requirements for hardware is significantly lower than the requirements for PoW. Initially, NIS can be run with minimum 512MB RAM. A Raspberry Pi would be good enough to run as a node. As the network grew, the requirements increased. At the time this is being written, at least 4GB RAM is recommended. Ideally, 8GB.  

*Prerequisites to run NIS:*  
• RAM: At least 4GB.  
• CPU: 1Ghz+ single core.  
• Internet Bandwidth: At least 5mbps of speed  
• TCP ports 7778, 7880, and 7890 open for inbound/outbound on firewalls and routers   
• Any minimal Linux distros  
• OpenSSH  
• Java 8  

2. After downloaded the “package” folder, go to “nis” folder in “package”, configure the following fields of cofig.properties.  
• *nis.bootKey:* Private key of an account for booting NIS. Use only private key of a delegated harvesting account. Using the private key of an account with mosaics might risk your mosaics being syphoned when the private key is compromised. Delegated harvesting account that has a good importance score would help the NIS to be picked up by other nodes for time synchronization.  
• *nis.bootName:* Name of the NIS. Will be shown on explorer. E.g. HugeTestAlice. NIS’s name will be shown in http://bob.nem.ninja:8765/#/nodes/.    
• *nis.shouldAutoHarvestOnBoot:* Set it to “true” for auto harvesting on boot.   

3. In order to allocate enough RAM for NIS, edit “nix.runNis.sh”. The following script allocate 4G RAM to NIS. (All in one line)  
 
`java –Xms4G –Xmx4G -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:+PrintGC - Xloggc:"./gc.txt" -cp ".:package/nis:package/nis/*:package/libs/*" org.nem.deploy.CommonStarter`  

4. To execute the NIS startup script, run the following command.  
`./nix.runNIS.sh`  

5. To sync the node  
The node can be synced manually. Depending on the RAM allocated, the speed of syncing varies, and it can take quite some time. Alternatively, download the latest [database dump](http://bob.nem.ninja/). At the point of this documentation is being written, ‘nis5_mainnet.h2-1680k.db.zip’.  
`wget http://bob.nem.ninja/nis5_mainnet.h2-1680k.db.zip`  

Unzip the file and move the extracted database dump into nem/nis/data folder at the root directory. Reboot the node.  

`unzip nis5_mainnet.h2-1680k.db.zip`
`mv nis5_mainnet.h2.db nem/nis/data/`

Once the NIS command is initiated and the blocks from the database is loaded, the node will be running live. Messages of harvester attempting to harvest a block will be popping up.  Go to YOUR-SERVER-IP:7890/node/extended-info to check if the node is updated. After the node has synced and live for some time, it will then show up on https://nemnodes.org/nodes/ with the node name provided in the config.properties file.  

`NOTE: To have the node on the node list, port forwarding on port 7870 need to be enabled on the router. Else it will still work but will not be shown on the node list.`

**What is API?**
API (Application programming Interface) is a set communication tools amongst sets of components. It makes objects usable outside of its original application and simplifies programming without the need to understand the actions happening behind the scenes.  

**What is JSON?**
[JSON](https://www.json.org/) (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999.”   

**Requests through RESTful APIs**
NIS uses port 7890 to communicate with its clients. Most GET requests can be done from browser.    

**APIs and JSONs for NEM Transactions**
The only way to change the account state is through a transaction. Through transaction, XEM and/or messages are transferred from one account to another, hence, altering the account state. In all the transactions, there are some fields that are a `must` before being included in a block, including:  

● timeStamp:  
  ● Measured in seconds, timeStamp recorded the time elapsed since Nemesis block on 29th March 2015.  
  ● It signifies the time of each transaction is made.  
  ● Future timestamp is not allowed. Error will return if future timestamp is detected.  
● signature:  
  Transaction signature is made of array of bytes extracted from the transaction. The array of bytes has different structure for different types of transactions. 2 important points to note while forming the signature:  
  ● when the field denotes a number, the endianness matters.  
  ● the order in which the fields are concatenated matters.  

`However, the “signature” field will not be available if the transaction is to be signed by NIS1 or if it is a multisig transaction and all the cosignatories required are yet to sign. This also mean the transaction is not ready to be included in a block.`

● fee:  
  ● Each transaction will have minimum fee of 0.05 xem even if there is no message and no xem is transferred in said transaction.  
  ● Higher transaction fee will get priority to be included in a block.  
  ● Insufficient funds will result in error message.  
● type:  
There are 8 types of transactions. Details will be discussed later of the chapter:  
  ● 0x101: Transfer of XEM from sender to recipient.  
  ● 0x801: Transfer of importance from sender to remote account.  
  ● 0x1001: An aggregate modification transaction, which converts a normal account into a multisig account.  
  ● 0x1002: A multisig signature transaction which is used to sign a multisig transaction.  
  ● 0x1004: A multisig transaction, which is used for multisig accounts.  
  ● 0x2001: Provision namespace transaction.  
  ● 0x4001: Mosaic definition creation transaction.  
  ● 0x4002: Mosaic supply change transaction.  
● deadline:  
  ● Measured in seconds, deadline is the time elapsed from Nemesis block. If the transaction doesn’t get included in a block upon the deadline, the transaction will be dropped.  
  ● Default dateline is 1 hour.  
  ● 24 hours is the maximum deadline.  
  ● Observing deadline is important for multisignature transactions.  
● version:  
Contains both the network version and the transaction version.   
Network version:  
  ● 0x98: the test network version  
  ● 0x68 : the main network version  
  ● 0x60 : the mijin network version  
Transaction version:  
  ● 0x01 version 1. For transaction of xem.
  ● 0x02 version 2. For transaction of mosaics. It can be used for transaction of xem too as xem is a mosaic too, native to NEM network. e.g. -1744830463 = 0x98000001 (network version 0x98 and transaction version 0x01)
● signer:
  Holds the public key of the account initiated the transaction, encoded as hexadecimal string.

Transactions is done through a `POST` request. There are 8 types of transactions: 

1. **0x101: (257)** Transfer of XEM from sender to recipient.  
The most common transaction in NEM network, refer to as Transfer Transaction. All transactions need to be signed, hence, signature is the mandatory field in a transaction. To sign a transaction, there are two ways: to have a NIS to sign it on behalf or to sign it at application level.  

`/transaction/prepare-announce`  

The NIS needs the transaction initiator’s private key in order to sign the transaction on behalf. Hence, it is very important that only TRUSTED and LOCAL nodes that the private key is sending to. Sending private key to untrusted node risks having the private key being compromised.  

The parameter for this API is RequestPrepareAnnounce:  
```JSON 
{
"transaction":
   {
  "timeStamp": 9111526,
"amount": 1000000000,
"fee": 50000,
"recipient": "TDGIMREMR5NSRFUOMPI5OOHLDATCABNPC5ID2SVA", "type": 257,
"deadline": 9154726, "message":
{
         "payload": "74657374207472616e73616374696f6e",
"type": 1 },
"version": -1744830463,
"signer": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
},
"privateKey": "68e4f79f886927de698df4f857de2aada41ccca6617e56bb0d61623b35b08cc0"
       }
```

Fields and the descriptions:  
● amount:  
The amount of xem that is sending over to the recipient. It is always stated in micro xem, i.e. 1000000 equals to 1 xem.    
● [fee:](https://nemproject.github.io/#transaction-fees)  
Every transaction incurs fee. The minimum fee is 0.05xem without message and amount less than 20,000 xem. The transaction fees for a certain block go to the harvester of that particular block. Details of fee calculation is available in 7.10 of NEM NIS API documentation.   
● recipient:  
The account address of the receiving party of the transaction. An error message will return if the address is not valid.  
● message:  
○ payload: Message is optional for a transaction. Payload is the actual message data.  
The maximum size for the payload is 1024 bytes. If the message exceeds the limit, an error message will be returned.  
○ type: Message can be encrypted, unencrypted or in hexadecimal form. For encrypted messages, 49 bytes are to be reserved for the encryption.  
● privateKey:  
The private key of the account signing the transaction.  

`/transaction/announce`  

The second method, sign the transaction before broadcasting the array and the corresponding signature to the NEM network via RequestAnounce object. This is a safer way as the initiator does not need to send the private key over to the node.  

```JSON 
{
"data": "010100000100000000000000200000002b76078fa709bbe6752222b215abc
  7ec0152ffe831fb4f9aed3e7749a425900a00093d000000000000000000280000
0054444e46555946584f5353334e4e4c4f35465a5348535a49354c33374b4e514 9454850554d584c54c0d45407000000000b00000001000000030000000c3215", "signature": "db2473513c7f0ce9f8de6345f0fbe773dc687eb571123d08eab4d98f96849e
aeb63fa8756fb6c59d9b9d0e551537c1cdad4a564747ff9291db4a88b65c97c10d”
 }
```

Fields and the descriptions:  
● data:  
The transaction data in the form of string. The string is created by first creating the corresponding byte array and then converting the byte array to a hexadecimal string.   

For every transaction broadcasted, there is a return [NemAnnounceResult](https://nemproject.github.io/#nemRequestResult).

```JSON  
{
"type":1,
 "code":1,
"message":"SUCCESS",
"transactionHash": { "data":"c1786437336da077cd572a27710c40c378610e8d33880bcb7bdb0a42e3d35586" },
"innerTransactionHash": {
"data":"NULL"
}
}
```

Fields and the descriptions:  
● type:   
The type of return depending on the request made.  
1: The result is a validation result.   
2: The result is a heartbeat result. 
4: The result indicates a status.  
● code:   
Error code for “type”. Refer to “code” description in 9.30 of [NEM NIS API Documentation](https://nemproject.github.io/#nemRequestResult).  
● message:  
Message about the error code.  
● transactionHash:  
○ data: The hash of the transaction.  
● innerTransactionHash:  
○ data: The hash of the transaction for multisig transaction. NULL if it is not a multisig
 transaction.  

Where there is an error, a JSON error object will be returned rather:  

Fields and the descriptions:  
● error:  
The general description of the error.  
● message:  
The detailed error message.  
● status:  
The HTTP status.  
The most common errors are:  
● The sender account has not enough funds.  
● The timestamp is invalid because it lies too far in the future.  
● The deadline is invalid because it has already been passed.  
● The attached message is too large.  
● The transaction is already known.  
● There is another transaction conflicting with this transaction. This can happen when trying to transfer the importance to another account.  

2. **0x801: (2049)** Transfer of importance from sender to remote account.  

Importance is transferred from one account to another for harvesting purposes.  

```JSON 
{
"timeStamp": 9108808,
"error": "Bad Request",
"message": "address must be valid", "status": 400
}
 {
"signature": "651a19ccd09c1e0f8b25f6a0aac5825b0a20f158ca4e0d78f2abd904a3966b6e3599a47b9ff199a3a6e1152231116f a4639fec684a56909c22cbf6db66613901",
"fee": 150000,
  "timeStamp": 9111526,
       "mode": 1,
"remoteAccount": "cc6c9485d15b992501e57fe3799487e99de272f79c5442de94eeb998b45e0144", "type": 2049,
"deadline": 9154726,
"version": 1744830465,
      }
"signer": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
```

Fields and the descriptions:  
● mode:    
This field signifies the harvesting request. There are only 2 modes:   
○ 1: Activate remote harvesting.  
○ 2: Deactivate remote harvesting.  
● remoteAccount:  
This field holds the public key of the receiving account in hexadecimal format.  

3. **0x1001: (4097)** An aggregate modification transaction  

This transaction converts a normal account into a multisig account.  

```JSON 
{
  "timeStamp": 9111526,
"fee": 28000000,
"type": 4097,
"deadline": 9154726,
"version": -1744830462,
"signer": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a", "modifications": [
{
"modificationType": 1, "cosignatoryAccount":
          "6083df7119d43e815ed2967c795f806f6b73f8f92a56a7611e3848816ec50958"
  },{
"modificationType": 1,
"cosignatoryAccount": "0662ed29cbfa7038530fb7f52df865eed6708d51bc7a24bcd05db35185b53c70"
},{
"modificationType": 1,
"cosignatoryAccount": "cc61676a4275abcffd10a9ea1081091ff054a1a8a720429256aebf8034aab099"
}
         ],
  "minCosignatories" : { "relativeChange": 2
}
   },
```

Fields and the descriptions:  
● modifications (MultisigConsignatoryModification object):   
○ modificationType:  
There are 2 types of modification:  
1: Add a new cosignatory  
2: Delete an exisiting cosignatory.  
○ cosignatoryAccount:
The public key of the cosignatory account in hexidecimal format.
● minCosignatories:
○ relativeChange: The relative change of the minimum cosignatories, i.e. the “m”.

4. **0x1004: (4100)** A multisig transaction, which is used for multisig accounts.  
A transaction from a multisig account being wrapped inside a multisig transaction.  

```JSON   
{
"timeStamp": 9111526,
"fee": 3000000,
"type": 4100,
"deadline": 9154726,
"version": -1744830463,
"signer": "6083df7119d43e815ed2967c795f806f6b73f8f92a56a7611e3848816ec50958", "otherTrans": {
"timeStamp": 9111526,
//initiator account
"amount": 1000000000,
"fee": 4000000,
"recipient": "TBJUSANZ63AKNJ57XMK6Y2IBH55UNNRXJFZRDTRW",
 "type": 257, "deadline": 9154726, "message":
{
"payload": "", "type": 1
//a transfertransaction
},
  "version": -1744830463,
"signer": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a" //multisig account
},
"signatures":[ // to include the information of co-signor.
] },
```

5. **0x1002: (4098)** A multisig signature transaction which is used to sign a multisig transaction.  

The cosignatories of a multisig transaction must know the hash of the inner transaction in order to be able to sign the multisig transaction. There are two ways of gaining knowledge of that hash:  

1. The initiator of the multisig transaction writes down the hash (which is included in the returned JSON object by NIS) and sends the hash to the cosignatories. The implementer of the client’s side software is responsible for transferring the hash to the cosignatories.  
2. The cosignatories poll the unconfirmed transactions using their local NIS. The meta data part of an unconfirmed transaction JSON object contains the hash of the inner transaction in case of a multisig transaction. The NEM network will take care of it.  

NemAnnounceResult object:  

```JSON 
{
"type": 1,
"code": 1,
"message": "SUCCESS" "transactionHash": {
"data":"c1786437336da077cd572a27710c40c378610e8d33880bcb7bdb0a42e3d35586" },
"innerTransactionHash": {
"data": "44e4968e5aa35fe182d4def5958e23cf941c4bf809364afb4431ebbf6a18c039"
} }
 {
"transaction":
{
"timeStamp": 9111526,
"fee": 6000000,
"type": 4098,
"deadline": 9157365,
"version": -1744830463,
"signer": "0662ed29cbfa7038530fb7f52df865eed6708d51bc7a24bcd05db35185b53c70",
  "otherHash": {
"data": "44e4968e5aa35fe182d4def5958e23cf941c4bf809364afb4431ebbf6a18c039"
},
"otherAccount": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS"
},
"privateKey": "00be34fdb20a9f6fed51376f0bab9f25ea7a48d610324588a6b203d0a1a6db4bc1" }
```

Fields and the descriptions:
● otherHash:
innerTransactionHash returned after the multisig transaction being broadcasted.
● otheAccount:
The address of the corresponding multisig account.

6. **0x2001: (8193)** A provision namespace transaction.  
Renting a namespace is done through ProvisionNamespaceTransaction object.   

```JSON 
{
31116fa4639fec684a56909c22cbf6db66613901", "fee": 150000,
"type": 8193,
 "transaction":
{
"timeStamp": 9111526,
   "signature":
 "651a19ccd09c1e0f8b25f6a0aac5825b0a20f158ca4e0d78f2abd904a3966b6e3599a47b9ff199a3a6e11522
 "deadline": 9154726,
  "version": -1744830463,
"signer": "d99e88c90da71a4b0d848454e59e296c9ef7a8f018f3eaa3a198dc460b6621a4",
  "rentalFeeSink": "3e82e1c1e4a75adaa3cba8c101c3cd31d9817a2eb966eb3b511fb2ed45b8e262",
  "rentalFee": 10000000, "newPart": "voucher", "parent": "alice"
},
     "privateKey": "00be34fdb20a9f6fed51376f0bab9f25ea7a48d610324588a6b203d0a1a6db4bc1" }  
```

Fields and the descriptions:  
● rentalFeeSink:  
The public key of the account to which the rental fee is to be transferred to.  
● rentalFee:  
The fee for renting the namespace. 100 xem for renting root namespace and 10 xem for renting sub-namespace. Rental for root namespace is yearly and sub-namespace rental is one-time payment.  
● newPart:  
It can be rootnamespace or sub-namespace that the account wants to rent. If it is a sub- namespace that the account is renting, it will be concatenated to the root namespace or level 1 sub-namespace with a “.” as a separator.  
● parent:  
It can be either root namespace or level 1 sub-namespace. It will be “null” if the account is renting a root namespace.  
The transaction will return an error if:  
● The the root namespace is not available, i.e. already rented by another account.  
● The namespace contains illegal character or a reserved namespace part.  
● The public key of the rental fee sink is invalid.    
● The rental fee is insufficient.  
To check if you are the owner of the namespace, use /account/namespaces request.  

7. **0x4001: (16385)** A mosaic definition creation transaction.  

To create mosaic, the MosaicDefinationCreationTransaction (in red) is needed.  

```JSON   
{
"timeStamp": 9111526, "signature":
"651a19ccd09c1e0f8b25f6a0aac5825b0a20f158ca4e0d78f2abd904a3966b6e3599a47b9ff199a3a6e1152231
     "fee": 150000,
"type": 16385,
"deadline": 9154726,
"version": -1744830463
"signer": "cbda3edb771d42801a5c6ce0725f9374efade19a8933d6ac22ccfa50c777d0f9", "creationFee": 10000000,
"creationFeeSink": "53e140b5947f104cabc2d6fe8baedbc30ef9a0609c717d9613de593ec2a266d3",
"mosaicDefinition": {
"creator": "cbda3edb771d42801a5c6ce0725f9374efade19a8933d6ac22ccfa50c777d0f9",
         116fa4639fec684a56909c22cbf6db66613901",
  "id": {
"namespaceId": "alice.vouchers",
"name": "Alice's gift vouchers"
   "description": "precious vouchers",
  "properties": [{
 "name": "divisibility",
 },
"value": "3"
  },{
},{
"name": "supplyMutable", "value": "false"
},{
"name": "transferable",
 "name": "initialSupply", "value": "1000"
       "value": "true"
  }
], "levy": {
"type": 1,
"recipient": "TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH", "mosaicId": {
      "namespaceId": "nem", "name": "xem"
},
   "fee": 1000 }
}
     }
```

Fields and the descriptions:  
● creationFee:  
Fee in micro xem for creating mosaic.  
● createFeeSink:  
The public key of the account to which the creation fee is to be transferred to.  
● mosaicDefinition:  
The mosaic definition (highlighted in red) of MosaicDefinition object.  
● creator:  
The public key of the account creating the mosaic.  
● id: Explained by the MosaicId (highlighted in blue).  
○ namespaceId: The corresponding namespace id where the mosaics attach to.  
○ name: The name of the mosaic definition.  
● description:  
The mosaic description, and it cannot be left empty. The maximum length is 512 characters.  
● properties:  
The properties of the mosaic which the details are encapsulate in MosaicProperties object (highlighted in green). The fields can be left empty where the default value will be applied.  
○ name:  
The name of the mosaic property. There are totally 4 of them.  
○ value:  
The value of each of the mosaic property.  
■ divisibility: Defines the smallest sub-unit of the mosaic. The mosaic can have 0 divisibility meaning it cannot be subdivided and the maximum of 6 divisibility. Default value is 0.  
■ initialSupply: Defines the initial amount of mosaic to be created, as a whole, rather than in sub-unit. The initial supply amount should be between 1 to 9,000,000,000. Default value is 1,000.  
■ supplyMutable: Determines if the supply of the total supply of the mosaic is mutable. The total supply of the mosaic can be changed by using MosaicSupplyChangeTransaction object. Default value is “false”.  
■ transferable: Defines if the mosaics are free to be transacted between accounts other than from the creator to an account, and from that account back to the creator. Default value is “true”.  
○ levy:  
The creator of the mosaic can demand a fee to be paid for transferring the mosaic.  
■ type: There are 2 types of transaction fees:  
● 1: Absolute fee. It defines the fixed micro-mosaic to be transferred to the recipient for each transaction.  
● 2: Percentile fee. It defines the percentage of total mosaics is to be transferred to the recipient, in micro-mosaic.  
■ recipient: The address of the recipient of the levy.  
■ mosaicId: The mosaic in which the levy is paid.  
● namespaceId: the namespace the mosaic corresponding to.  
● name: the name of the mosaic used to pay for the levy.  
■ fee: Depends on the “type”, it is either the fixed micro-mosaic or the percentile.  

8. **0x4002: (16386)** A mosaic supply change transaction.  
To change the supply of the mosaic, only if “supplyMutable” is set to “true” when the mosaic is being created, a MosaicSupplyChangeTransaction object is needed.  

```JSON 
{
 "timeStamp": 9111526, "signature":
  "651a19ccd09c1e0f8b25f6a0aac5825b0a20f158ca4e0d78f2abd904a3966b6e3599a47b9ff199a3a6e1152231
  116fa4639fec684a56909c22cbf6db66613901", "fee": 150000,
"type": 16386,
"deadline": 9154726,
"version": -1744830463,
     }
"signer": "d99e88c90da71a4b0d848454e59e296c9ef7a8f018f3eaa3a198dc460b6621a4",
     "supplyType": 1, "delta": 123, "mosaicId": {
"namespaceId": "alice.vouchers",
"name": "gift vouchers" }
```

Fields and the descriptions:  
● supplyType:  
The total supply can be increase or decrease.  
○ 1: Increase in supply.  
○ 2: Decrease in supply.  
● delta:  
The amount to be increased or decreased.  
● MosaicId:  
The ID of the mosaic which supply is to be changed.  
The transaction may not be accepted by NIS due to:   
● The transaction signer is not the creator of the mosaic.  
● The “supplyMutable” is set to “false”.  
● The total supply exceeded 9,000,000,000.  
● The total amount of mosaics the creator owns is lesser than the amount the creator wants to decrease/delete.  

**Monitoring Blockchain**  
Transactions that are being broadcasted to the network are not being confirmed immediately. To keep track on the block confirmation, there are 2 ways to [monitor the blockchain](https://rb2nem.github.io/nem-dev-guide/07-monitoring-blockchain/) for updates.   

1. Active monitoring: Pooling approach  

2. Passive monitoring: Subscription approach  
