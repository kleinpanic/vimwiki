# KPChat 

## Overview: 
1. 

2. Security: 
   * End-to-End Encryption (E2EE): All messages exchanged between users should be encrypted on the sender's device and decrypted only on the recipient's device. 
   * Local storage Encryption: User data, including credentials and chat history, should be stored locally in an encrypted format. 
        * Explore tools like libsodium or OpenSSL for encryption along with encrypted file systems. 
    * Authentication: Add a secure way to handle user Authentication. Password based authentication, hash and salt passwords
        * Libs like bcrypt. 
    * Decentralization: Instead of a central server to manage user info and messages, a P2P, or federated architecture where each client acts as both a server and a client. 
      
3. Network Architecture 
    * Peer-to-Peer (P2P):
        * Each instance of the app directly connects to other instances (peers). This allows decentraization and removes the need for a central server.
        * Challenges: How will peers discover each other? How do you handle peer-to-peer connectivity in different networks (NAT traversal, )?, potentially add protocols like WebRTC, DHT(Distributed Hash Table), or libp2p for managing peer discoverying and communication.
        * Encryption between peers is essential to secure data transmission.
    * Federated Architecture: 
        * instead of a single central sever, you could have multiple nodes that can communicate with each other. Each node would be responsible for manaing its users' data, acting as both server and client. 
        * Challenges: Keeping messages synchronized between nodes while keeping data secure and avoiding centralized data collection is tricky.

4. Authentication & Account Management
    * Account Creation: Since there's no central database, each local instance would need to manage its user accounts. When a user creates an account, the app could generate a public-private keypair. The public key is shared with other users, while the private key remains secure on the user's device. This keypair can be used for:
        * Encryption: Encrypting/decrypting messages.
        * Authentication: Verifying the user identity without relying on a central authority.
    * Passsword Management: Storing passwords securely is important. bcrypte for ahasing and salting pswords can be useful. 

5.  Decentralization Model
    * Peer-to-Peer (P2P): Users directly connect to one another. Each client maintains a list of their peers and messages are exchanged directly.
    * Local First: Each user stores their own data locally. You could use gossip protocols to synchronize information between peers. This is how many modern distributed systems (like blockchains) work.
    * Hybrid Model: Some components, like peer discovery, can be centralized (e.g., a DHT or STUN servers), while actual messaging remains P2P.
6. Message Exchange and Encryption

    * End-to-End Encryption: Public-private key cryptography (using something like RSA or ECDSA) will allow you to encrypt messages sent between users. When a message is sent, the sender encrypts it using the recipient's public key, ensuring that only the recipient can decrypt it with their private key.
    * Symmetric Key Encryption: For efficiency, after establishing a connection between peers, symmetric key algorithms like AES can be used for the ongoing communication, as it's faster than public-key encryption.

7. Offline Message storage 
Since each user stores their data locally, you might face challenges with offline messaging. Some possibilities:
    * Message Queueing: If a peer is offline, you could store messages locally, and once the peer comes online, these messages are sent. This would require reliable peer discovery.
    * Encrypted Local Storage: To ensure security, even if someone accesses the local system, all messages should be stored encrypted on the local file system.

