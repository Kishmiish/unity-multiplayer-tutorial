# Introduction to Networking Concepts for Multiplayer Games in Unity

## 1. Network Communication Models

There are two common models for connecting devices over a network:

### **Client-Server Model**
In this model, a central device (the server) coordinates communication, and all other devices (clients) connect to it.
- **Pros**: Centralized control, better synchronization, improved security.
- **Cons**: High server load, requires hosting infrastructure.

### **Peer-to-Peer (P2P) Model**
All devices communicate directly with each other and share equal responsibility.
- **Pros**: Distributed load, no need for a central server.
- **Cons**: Harder to coordinate, more complex security and implementation.

> Unity Netcode for GameObjects uses the **Client-Server** model with an additional concept called **Host**, which acts as both a client and a server at the same time.

---

## 2. Communication Protocols

When sending data over the network, two main protocols are used:

### **TCP (Transmission Control Protocol)**
- Reliable, connection-based communication.
- Guarantees data delivery in the correct order.
- Slower, but more accurate.

### **UDP (User Datagram Protocol)**
- Fast, connectionless communication.
- No guarantee that data will arrive or arrive in order.
- Commonly used in games where speed is critical.

> Multiplayer games often use **UDP** to prioritize speed and responsiveness.

---

## 3. Key Concepts in Multiplayer Game Development

When building multiplayer games, you will frequently deal with the following terms:

### **Networked Object**
An object whose state must be shared across all players, such as a character’s position, health, or projectiles.

### **State Synchronization**
The process of updating and sharing the state of objects (e.g., position, rotation, health) between the server and all clients to keep them in sync.

### **RPC (Remote Procedure Call)**
A way to invoke a function on another machine through the network. Unity’s Netcode provides:
- **ServerRPC**: Called from a client to request the server to do something.
- **ClientRPC**: Called from the server to instruct clients to do something.
- **ObserversRPC**: Called from the server to clients who are observing a specific object.

### **Ownership**
Determines which client is responsible for controlling and updating a specific networked object (usually the player controls their own character).

---

## 4. Other Technical Concepts

- **NetworkObject**: A component that turns a GameObject into a network-synchronized object.
- **NetworkBehaviour**: A script attached to a NetworkObject that contains networked logic and RPCs.
- **Transport Layer**: The part of the system responsible for sending and receiving data. Unity supports various transport systems like Unity Transport, ENet, etc.
- **Latency & Lag**: The delay between sending and receiving data over the network, which can affect gameplay.