Hypertext Transfer Protocol Secure is a protocol that is used to communicate between the user browser and the website. It also helps in the transfer of data. It is the secure variant of HTTP. To make the data transfer more secure, it is encrypted. Encryption is required to ensure security while transmitting sensitive information like passwords, contact information, etc.

## HTTP vs HTTPS

Below are the basic differences between the HTTP and HTTPS.

| HTTP                                                                                                  | HTTPS                                                                                              |
| ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| HTTP stands for HyperText Transfer Protocol.                                                          | HTTPS stands for HyperText Transfer Protocol Secure.                                               |
| URL begins with “http://”.                                                                            | URL starts with “https://”.                                                                        |
| HTTP Works at the [Application Layer](https://www.geeksforgeeks.org/application-layer-in-osi-model/). | HTTPS works at [Transport Layer](https://www.geeksforgeeks.org/transport-layer-responsibilities/). |
| HTTP speed is faster than HTTPS.                                                                      | HTTPS speed is slower than HTTP.                                                                   |
## How Does HTTPS Work?

HTTPS establishes the communication between the browser and the web server. It uses the ***Secure Socket Layer** (SSL) and **Transport Layer Security** (TLS) protocol for establishing communication. The new version of SSL is **TLS(Transport Layer Security)**.

## Secure Socket Layer (SSL)

The main responsibility of SSL is to ensure that the data transfer between the communicating systems is ***secure and reliable****. It is the standard security technology that is used for encryption and decryption of data during the transmission of requests.

As discussed earlier, HTT PS is basically the same old HTTP but with SSL. For establishing a secure communication link between the communicating devices, SSL uses a digital certificate called ***SSL certificate****. 

There are two major roles of the SSL layer

- Ensuring that the browser communicates with the required server directly.
- Ensuring that only the communicating systems have access to the messages they exchange.
## Encryption in HTTPS

HTTP transfers data in a hypertext format between the browser and the web server, whereas HTTPS transfers data in an encrypted format. As a result, HTTPS protects websites from having their information broadcast in a way that anyone eavesdropping on the network can easily see. During the transit between the browser and the web server, HTTPS protects the data from being accessed and altered by hackers. Even if the transmission is intercepted, hackers will be unable to use it because the me ssage is encrypted.

It uses an asymmetric public key infrastructure for securing a communication link. There are two different kinds of keys used for encryption – 

- ***Private Key****: It is used for the decryption of the data that has been encrypted by the public key. It resides on the server-side and is controlled by the owner of the website. It is private in nature.
- ***Public Key****:  It is public in nature and is accessible to all the users who communicate with the server. The private key is used for the decryption of the data that has been encrypted by the public key.
## Advantage of HTTPS

- ***Secure Communication:*** HTTPS establishes a secure communication link between the communicating system by providing encryption during transmission.
- ***Data Integrity:*** By encrypting the data, HTTPS ensures data integrity. This implies that even if the data is compromised at any point, the hackers won’t be able to read or modify the data being exchanged.
- ***Privacy and Security:** HTTPS prevents attackers from accessing the data being exchanged passively, thereby protecting the privacy and security of the users.
- ***Faster Performance:*** TTPS encrypts the data and reduces its size. Smaller size accounts for faster data transmission in the case of HTTPS.
--------------------------------------------------------------------------
# [The information is taken from the GeeksforGeeks](https://www.geeksforgeeks.org/what-is-http/)
