***HTTP (Hypertext Transfer Protocol) is a fundamental protocol*** of the Internet, enabling the transfer of data between a client and a server. It is the foundation of data communication for the World Wide Web.

HTTP provides a standard between a web browser and a web server to establish communication. It is a set of rules for transferring data from one computer to another. Data such as text, images, and other multimedia files are shared on the World Wide Web. Whenever a web user opens their web browser, the user indirectly uses HTTP. It is an application protocol that is used for distributed, collaborative, hypermedia information systems.

## Methods of HTTP

- ***GET****: Used to retrieve data from a specified resource. It should have no side effects and is commonly used for fetching web pages, images, etc.
- ***POST****: Used to submit data to be processed by a specified resource. It is suitable for form submissions, file uploads, and creating new resources.
- ***PUT****: Used to update or create a resource on the server. It replaces the entire resource with the data provided in the request body.
- ***PATCH****: Similar to PUT but used for partial modifications to a resource. It updates specific fields of a resource rather than replacing the entire resource.
- ***DELETE****: Used to remove a specified resource from the server.
- ***HEAD****: Similar to GET but retrieves only the response headers, useful for checking resource properties without transferring the full content.
- ***OPTIONS****: Used to retrieve the communication options available for a resource, including supported methods and headers.
- ***TRACE****: Used for debugging purposes to echo the received request back to the client, though it's rarely used due to security concerns.
- ***CONNECT****: Used to establish a tunnel to the server through an HTTP proxy, commonly used for SSL/TLS connections.
## HTTP Request/Response:

HTTP is a request-response protocol, which means that for every request sent by a client (typically a web browser), the server responds with a corresponding response. The basic flow of an HTTP request-response cycle is as follows:

- ***Client sends an HTTP request****: The client (usually a web browser) initiates the process by sending an HTTP request to the server. This request includes a request method (GET, POST, PUT, DELETE, etc.), the target URI (Uniform Resource Identifier, e.g., a URL), headers, and an optional request body.
- ***Server processes the request****: The server receives the request and processes it based on the requested method and resource. This may involve retrieving data from a database, executing server-side scripts, or performing other operations.
- ***Server sends an HTTP response:**** After processing the request, the server sends an HTTP response back to the client. The response includes a status code (e.g., 200 OK, 404 Not Found), response headers, and an optional response body containing the requested data or content.
- ***Client processes the response****: The client receives the server's response and processes it accordingly. For example, if the response contains an HTML page, the browser will render and display it. If it's an image or other media file, the browser will display or handle it appropriately.
## HTTP Request Circle

| Requested Resource | Resource Type   | Server Response            |
| ------------------ | --------------- | -------------------------- |
| HTML Page          | HTML            | Server sends HTML file     |
| Style Sheet (CSS)  | CSS             | Server sends CSS file      |
| Image (JPG)        | Image (JPG)     | Server sends JPG image     |
| JavaScript Code    | JavaScript (JS) | Server sends JS file       |
| Data (XML or JSON) | Data            | Server sends XML/JSON data |
## Advantages

- ***Platform independence****: Works on any operating system
- **Compatibility****: Compatible with various protocols and technologies
- **Efficiency****: Optimized for performance
- **Security****: Supports encryption for secure data transfer

## Disadvantages

- ***Lack of security****: Vulnerable to attacks like man in the middle
- **Performance issues:**** Can be slow for large data transfers
- ***Statelessness****: Requires additional mechanisms for maintaining state
--------------------------------------------------------------------------
# [The information is taken from the GeeksforGeeks](https://www.geeksforgeeks.org/what-is-http/)
