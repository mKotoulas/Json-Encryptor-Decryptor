# Json-Encryptor-Decryptor
Code snippets to encrypt JSON data in node.js with crypto and decrypt them in javascript using crypto-js. The encryption method being used is aes-256 under CBC mode. 

# HTTPS vs HTTP
When using an HTTPS connection between a client and a service, data being transmitted between them, are being encrypted by the protocol itself using encryption protocols such as TLS. This means that a third party that somehow monitors data being transmitted between client and server is unable to decrypt and hence make sense of that data. When an HTTPS connection is established, and before any actual data is transmitted on the network, the client and server negotiate encryption keys, certificates, etc resulting in no plain data being exchanged on the network. For someone to be able to decrypt the data being exchanged, it is a requirement to possess the information in the previous handshake phase, which practically means that one has access to the network, the client or server is running on, and probably the ability to reroute the connection to its network rather than the server's one. In general, HTTPS is considered safe while the data is traveling on the network, and in most cases, no additional encryption of the data is needed. 

On the other hand, when using an HTTP connection in the above scenario, no encryption of the data is being used by the protocol itself meaning that data travel over the network in plain text making them directly accessible to a third party that monitors the communication between the server and the client. When using HTTP protocol, encryption of the data, if needed, should be manually added by the programmer.

# 


