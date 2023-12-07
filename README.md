# Json-Encryptor-Decryptor
Code snippets to encrypt JSON data in node.js with crypto and decrypt them in javascript using crypto-js. The encryption method being used is aes-256 under CBC mode using a random iv vector while the encrypted JSON is then encoded in a base-64 string   

# What it does
When working on a new service, it is a common need to simulate all HTTP(s) available methods your under-construction server is going to handle. While browsers are an option to simulate GET requests,  unless you use some extension, they don't typically provide an interface to do the same with the other methods. A widely used tool for cases like that is POSTMAN. Apart from that functionality, POSTMAN lets you code scripts that execute right before sending the request to the server or right after the response from the server has been received which extends the use cases of the tool. 


While not a necessity under HTTPS connections, you may want to encrypt the data being exchanged between server and client either because you use HTTP protocol instead of HTTPS or because you want to add an extra layer of protection, or because you are interested not only in security over the network but also in security in both ends. I added a little bit to that part in the next section. 

The above scenario can be implemented using a great variety of frameworks, tools, programming languages, and encryption algorithms combinations. The snippets in this repo, demo how you can implement the functionality of encrypting a JSON object, which is a very common type of a response or request body, both on the client and the server side, using the symmetric aes-256 encryption algorithm under the CBC mode (a random iv will be used in the encryption possess) with the server being a node.js express server and the client side being simulated by the POSTMAN tool described in the above paragraph. The encrypted JSON will be sent as a base-64 encoded string over the network.      

The encryption/decryption processes of the algorithm are implemented on the server side using the npm package crypto while the encryption/decryption processes are implemented on the client side (simulated by POSTMAN) using the javascript's crypto-js package. The reason behind the different implementations on the two sides is the fact that natively POSTMAN runs Javascprit and the crypto package is not available in that environment and vice versa , crypto-js is not a node.js compatible package. 





# HTTPS vs HTTP
When using an HTTPS connection between a client and a service, data being transmitted between them, are being encrypted by the protocol itself using encryption protocols such as TLS. This means that a third party that somehow monitors data being transmitted between client and server is unable to decrypt and hence make sense of that data. When an HTTPS connection is established, and before any actual data is transmitted on the network, the client and server negotiate encryption keys, certificates, etc resulting in no plain data being exchanged on the network. For someone to be able to decrypt the data being exchanged, it is a requirement to possess the information in the previous handshake phase, which practically means that one has access to the network, the client or server is running on, and probably the ability to reroute the connection to its network rather than the server's one. In general, HTTPS is considered safe while the data is traveling on the network, and in most cases, no additional encryption of the data is needed. 
On the other hand, when using an HTTP connection in the above scenario, no encryption of the data is being used by the protocol itself meaning that data travel over the network in plain text making them directly accessible to a third party that monitors the communication between the server and the client. When using HTTP protocol, encryption of the data, if needed, should be manually added by the programmer.

# Usage of the snippets 
With that being said, the usage of this repo snippets seems to have not a practical use not to mention that they add additional overhead to both sides as a result of the encryption-decryption processes.     


