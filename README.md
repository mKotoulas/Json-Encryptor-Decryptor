# Json-Encryptor-Decryptor
Json-Encryptor-Decryptor is a utility for securely encrypting and decrypting JSON data. The encryption method employed is AES-256 in CBC mode, utilizing a random initialization vector (IV). The encrypted JSON is further encoded into a base-64 string for ease of transmission and storage.

# What it does
When developing a new service, it is often necessary to simulate all available HTTP(s) methods that your under-construction server is going to handle. While browsers can be used to simulate GET requests, they may not provide an interface for other methods without extensions. POSTMAN is a widely used tool for such cases, offering the ability to simulate various HTTP methods. Additionally, POSTMAN allows the execution of scripts before sending a request or after receiving a response, expanding its use cases.

Even under HTTPS connections, encrypting the exchanged data between the server and the client can be desired for various reasons, such as using HTTP instead of HTTPS, adding an extra layer of protection, or ensuring security at both ends. The next section discusses the implementation of encrypting a JSON object, a common type of request or response body. This is demonstrated in this repository using the symmetric AES-256 encryption algorithm in CBC mode, with a random IV for encryption. The server is implemented using Node.js and Express, while the client side is simulated using POSTMAN.

The encryption/decryption processes on the server side are implemented using the npm package crypto. On the client side (simulated by POSTMAN), the encryption/decryption processes use the crypto-js package. This distinction arises from the fact that POSTMAN runs JavaScript natively, and the crypto package is unavailable in that environment. Conversely, crypto-js is not compatible with Node.js.





# HTTPS vs HTTP
When establishing an HTTPS connection between a client and a service, the data being transmitted undergoes encryption through protocols such as TLS. This encryption ensures that any third party attempting to monitor the communication is unable to decrypt and comprehend the transmitted data. The HTTPS handshake, which occurs before any actual data is exchanged, involves the negotiation of encryption keys and certificates between the client and server. Consequently, no plain data is sent over the network during this process. Decrypting the exchanged data would require access to the information generated in the handshake phase, implying control over the network the client or the server is running on, and potentially the ability to reroute the connection. In general, HTTPS is considered secure during data transmission, and in most cases, no additional encryption is deemed necessary.

Conversely, when using an HTTP connection in the same scenario, the protocol itself does not provide data encryption. As a result, information travels over the network in plain text, making it directly accessible to any third party monitoring the communication between the server and the client. In situations where encryption is necessary, such as when using the HTTP protocol, it becomes the responsibility of the programmer to manually implement additional encryption measures.




# Usage of the snippets 
With that said the snippets in this repository may not have a practical use, given that HTTPS already provides similar functionality, albeit with added overhead due to encryption-decryption processes on both ends.

However, it's crucial to recognize that HTTPS encryption ensures data security during transmission between the two ends, which is distinct from safeguarding data when it is at rest on one end. Assuming there are no additional communication nodes between the server and client is a simplification, and if present, data may undergo decryption-encryption processes at each node. Additionally, internal traffic between the load balancer and the server poses a potential vulnerability, as data is in a transit state and not encrypted.

Without delving into detailed intricacies, it's essential to acknowledge that even with HTTPS connections between clients and servers, there remain points of vulnerability in the communication cycle, where data may be stored or transmitted without encryption.

End-to-end encryption, encrypting data at the point of creation and only decrypting it at the point of use, irrespective of the underlying network protocol, addresses these concerns. The code snippets in this repository aim to facilitate this approach using the setup outlined in the previous section.






# How to use

 



