# P2P_RMB_protocol
A Peer-to-Peer communication protocol for Remote Message Bus

The purpose of this project is to establish a completely decentralized, peer to peer communication protocol for RMB Clients and Agents.

## Infrasture

The RMB is the communication agent, Vlang handlers are 

### Remote Message Bus

The remote message bus is a bus for messaging between RMB clients and agents.

- RMB Client: lives in browser, relays message to rmb agent over tf grid.
- RMB Agent: lives in node, users own agent, can relay message to other agent.

### Vlang RMB Handlers

The RMB agents in this protocol getting rmb messages from the client and converting them to actions are handlers. The vlang handler then translates this action to commands that it gives out to the rust underlayer.

### Rust Underlayer

Where gossipping, blockchain actions, happens. The p2p infrastructure.

## Protocol

User events in browser trigger RMB client to relay messages to their RMB Agent. User's public key is used to identify user's own RMB Agent. User's RMB Agent handles the RMB message it receives, and starts gossiping in accordance. The user's RMB Agent communicates with other RMB Agents through gossip protocols, to find contacts that fit user's criteria. 

### Gossip Protocol

Addresses of neighboring agents are known. The RMB Agent sends out the message to neighbors, and neighbors send out the message to their neighbors. 
Caches in agents allow for easy access to tag based searching.

[Rust gossip crate](https://docs.rs/gossip/latest/gossip/)

### imAlive

Agents notify the network that they're alive in a speicifed frequency. imlive ensures broken agents are removed from contact lists.

### Reputation

Reputation damaging activities are also gossipped, and neighboring agents cache the reputation of the corrupt agent.

### Caching & hashing

When RMB Agents that satisfy and respond to the broadcast are found, the conditions and resulting agent address is cached by the resulting agents neighboring agents. This allows for quicker results and keeping track of reputation. 

It is like asking your neighbor for a barber and your neighbor remembering a barber that another friend of theirs went to and trusted.

The table looks something like:

Public key | Address | Tag | Reputation |

## P2P Cryptocurrency Exchange

- When a user is looking to sell a cryptocurrency in exchange for another cryptocurrency, the data of the exchange request is registered to the RMB Agent.
- The Buyer Agent gossips their request to buy in increments of 1000$. 
- Once the buyer agent finds the seller, if the agents agree on terms, the exchange protocol is initiated (see below).
- The exchange agent validates that both parties agree on the exchange and executes an atomic swap between TF Grid and other blockchain.

### Exchange Protocol

- To ensure fairness, once the seller agent receives the request, a waiting period is initiated. This allows for the seller to receive other offers and prioritize them to preference. The nearest agent who gossiped to the seller the fastest does not have an advantage over others.
- The seller relays back an answer confirming or denying the transaction. 
- If the seller agrees to the terms of the exchange, the seller agent relays a rmb message to the Rust underlayer giving out the order to initiate the  exchange.
- The Rust underlayer creates and signs the contract, and relays the transaction id to the buyer agent.
- The buyer agent authenticates the contract and signs, and the contract signed by both parties is relayed to the Rust underlayer.
- The Rust underlayer authenticates the signatures of both parties and initiates the atomic swap. (do we need a timelock here to stop other synchronous exchanges or is htlc in atomic swap sufficient?)

## Going forward

Going forward this protocol will be used by the digital twin system to become the protocol for trading and exchanging information between twins, vendors etc.




