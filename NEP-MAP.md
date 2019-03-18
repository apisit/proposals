## Abstract
This NEP proposes a message inbox protocol to provide a standard mechanism for blockchain client to send messages or retrieve messages from a NEO blockchain network.

## Motivation
TODO: fill more detail here

## Specification
This proposal makes use of the following functions and definitions:

TODO: fill more detail here
- AES256Encrypt
- AES256Decrypt
- P256 ECDH
- SHA256
- Shamir's Secret Sharing algorithm over GF(2^8)

## Inbox message protocol
[WIP] It is the senders responsibility to encrypt a message. 

## Message access protocol
[WIP]  Message Access Protocol is an application layer blockchain protocol that allows a wallet client to access message from a blockchain node.  
Because message is encrypted using a shared secret between sender and receiver, Nobody in between can read the message or tamper with it. Only a true receiver of a message can read a decrypted message.

### Example use case
- Get notified about a certain event from a smart contract.
- An secure inbox to receive a message from someone.

### Methods

**Note: Every PublicKey field requires SHA-256(SHA-256(PublicKey))**

#### Register a sender
```public bool registerSender(senderPublicKey, info)```  
A sender register his/her public key with the smart contract. (we might not need this one)

#### Sender info
```public Sender senderInfo(senderPublicKey) ```  
Get a sender info with a public key.

#### Inbox
```public [](Hash256, senderInfo) inbox(receiverPublicKey)```  
A list of IDs of unread messages inside an inbox. 

#### Message
```public Message message(messageHash256)```  
Get message by ID. Due to a nature of blockchain and smart contract. anyone can get a storage value if the key is known. however, the data is encrypted.

#### Post message
```public bool post(senderPublicKey, receiverPublicKey, version, message)```  
Post a message to a receiver's inbox.

Optionals TBD

#### Broadcast
```public bool broadcast(senderPublicKey, topic, version, message)```  
Post a message to topic's inbox.

#### Subscribe
```public bool subscribe(subscriberPublicKey, topic)```  
Subscribe to a topic to receive message sent to a topic.

#### Unsubscribe
```public bool unsubscribe(subscriberPublicKey, topic)```  
Unsubscribe from a topic. 

#### Block
```public bool block(senderPublicKey, inboxOwnerPublicKey)```  
Block a sender from sending message to your inbox
