# Json-Encryptor-Decryptor
Code snippets to encrypt JSON data in node.js with crypto and decrypt them in javascript using crypto-js. The encryption method being used is aes-256 under CBC mode using a random iv vector while the encrypted JSON is then encoded in a base-64 string   

# What it does
When developing a new service, it is often necessary to simulate all available HTTP(s) methods that your under-construction server is going to handle. While browsers can be used to simulate GET requests, they may not provide an interface for other methods without extensions. POSTMAN is a widely used tool for such cases, offering the ability to simulate various HTTP methods. Additionally, POSTMAN allows the execution of scripts before sending a request or after receiving a response, expanding its use cases.

Even under HTTPS connections, encrypting the exchanged data between the server and client can be desired for various reasons, such as using HTTP instead of HTTPS, adding an extra layer of protection, or ensuring security at both ends. The next section discusses the implementation of encrypting a JSON object, a common type of request or response body. This is demonstrated in this repository using the symmetric AES-256 encryption algorithm in CBC mode, with a random IV for encryption. The server is implemented using Node.js and Express, while the client side is simulated using POSTMAN.

The encryption/decryption processes on the server side are implemented using the npm package crypto. On the client side (simulated by POSTMAN), the encryption/decryption processes use the crypto-js package. This distinction arises from the fact that POSTMAN runs JavaScript natively, and the crypto package is unavailable in that environment. Conversely, crypto-js is not compatible with Node.js.





# HTTPS vs HTTP
When establishing an HTTPS connection between a client and a service, the data being transmitted undergoes encryption through protocols such as TLS. This encryption ensures that any third party attempting to monitor the communication is unable to decrypt and comprehend the transmitted data. The HTTPS handshake, which occurs before any actual data is exchanged, involves the negotiation of encryption keys and certificates between the client and server. Consequently, no plain data is sent over the network during this process. Decrypting the exchanged data would require access to the information generated in the handshake phase, implying control over the network, the client, or server, and potentially the ability to reroute the connection. In general, HTTPS is considered secure during data transmission, and in most cases, no additional encryption is deemed necessary.

Conversely, when using an HTTP connection in the same scenario, the protocol itself does not provide data encryption. As a result, information travels over the network in plain text, making it directly accessible to any third party monitoring the communication between the server and the client. In situations where encryption is necessary, such as when using the HTTP protocol, it becomes the responsibility of the programmer to manually implement additional encryption measures.





On the other hand, when using an HTTP connection in the above scenario, no encryption of the data is being used by the protocol itself meaning that data travel over the network in plain text making them directly accessible to a third party that monitors the communication between the server and the client. When using HTTP protocol, encryption of the data, if needed, should be manually added by the programmer.

# Usage of the snippets 
With that being said, the usage of this repo snippet's seems to have not a practical use since HTTPS offers the same functionality , not to mention that they add additional overhead to both sides as a result of the encryption-decryption processes.



However it is important to understand that HTTPS encryption mechanisms are keeping data safe when in transition between the two ends which is a different thing from keeping data secure when they rest in one end. It is also a simplification to assume that there are no additional nodes of communication between the server and the client and if this is the case, data will be decrypted - encrypted in each node. Another thing that may be a problem is the internal traffic between the load balancer and the server where data are in a transit state and not encrypted.


To reach a point without going deeper in the details , when using HTTPS connections between clients and servers there are still points of attacks in the communication cycle i.e points where the data are being stored or transmitted without being encrypted.

Encrypting data to be transmitted in the time of their creation and only decrypting that data at the point of use , regardless of the underlying network protocol , is called end-to-end encryption and the code snippets in this repo attempt to help in that direction using the setup stated in the above section. 

# How to use

 



