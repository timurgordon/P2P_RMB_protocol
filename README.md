# P2P_RMB_protocol
A Peer-to-Peer communication protocol for Remote Message Bus

The purpose of this project is to establish a completely decentralized, peer to peer communication protocol for RMB Clients and Agents.

## Remote Message Bus

The remote message bus is a bus for messaging between RMB clients and agents.

Definitions
- RMB Client: lives in browser, relays message to rmb agent over tf grid.
- RMB Agent: lives in node, users own agent, can relay message to other agent.

## Protocol

User events in browser trigger RMB client to relay messages to an RMB Handler. User's public key is used to identify and relay client messages to user's own RMB Agent. User's RMB Agent handles the RMB message it receives and performs necessary actions. The user's RMB Agent communicates with other RMB Agents through gossip protocols. 

### Gossip Protocol

The RMB Agent sends out the message to neighbors, and neighbors send out the message to their neighbors.

#### Address Caching

Address

### Agent-Blockchain

#### Defi Wallet

##### Rust Bridge


## Going forward


```mermaid

```

