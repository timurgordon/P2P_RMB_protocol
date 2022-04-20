# P2P_RMB_protocol
A Peer-to-Peer communication protocol for Remote Message Bus

The purpose of this project is to establish a completely decentralized, peer to peer communication protocol for RMB Clients and Agents.

## Remote Message Bus

The remote message bus is a bus for messaging between RMB clients and agents.

- RMB Client: lives in browser, relays message to rmb agent over tf grid.
- RMB Agent: lives in node, users own agent, can relay message to other agent.

## Protocol

```mermaid

```

User events in browser trigger RMB client to relay messages to their RMB Agent. User's public key is used to identify user's own RMB Agent. User's RMB Agent handles the RMB message it receives, and starts gossiping in accordance. The user's RMB Agent communicates with other RMB Agents through gossip protocols, to find contacts that fit user's criteria. 

### Gossip Protocol

Addresses of neighboring agents are known. The RMB Agent sends out the message to neighbors, and neighbors send out the message to their neighbors. 
Caches in agents allow for easy access to tag based searching.

### isAlive

Is alive ensures broken agents are removed from contact lists.

### Reputation

Reputation damaging activities are also gossipped, and neighboring agents cache the reputation of the corrupt agent.

### Caching & hashing

When RMB Agents that satisfy and respond to the broadcast are found, the conditions and resulting agent address is cached by the resulting agents neighboring agents. This allows for quicker results and keeping track of reputation. 

It is like asking your neighbor for a barber and your neighbor remembering a barber that another friend of theirs went to and trusted.

The table looks something like:

Tag | Reputation | Public key | Address

## P2P Cryptocurrency Exchange

- An RMB Agent looking to sell a cryptocurrency in exchange for another cryptocurrency, the data is registered to the RMB Agent. (Optionally we may choose to gossip to first degree contacts for caching) 
- The Buyer Agent gossips their request to buy in increments of 1000$ (can change). Once the buyer agent finds the seller, if the agents agree on terms, both reach out to an exchange agent built on rust via RMB.
- The exchange agent validates that both parties agree on the exchange and executes an atomic swap between TF Grid and other blockchain.

## Going forward

Going forward this protocol will be used by the digital twin system to become the infrastructure for trading and exchanging information between twins, vendors etc.




