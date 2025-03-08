# Rest API- Representational state Transfer
- it's a web based application programming interface
- that follows the rest architectural style
- the primary purpose of rest is to provide an architecture for building web services that can be consumed by various clients, including web, mobile and desktop applications
- it is based on http, which is the standard protocol used for communication on the internet, it uses the http methods, including get,post,put,delete etc
- each resource in rest is identified by a unique url, and the response is returned in json or xml format
- 
-  it follows the stateless client-server model - this means that the server doesn't store any information about the client's state between requests
### When to use?
- this rest api is an excellent choice when buidling web services that require a stateless, scalable and easy to maintain architecture
- it is ideal for buidling applications that require crud operations




# Web API - 
- web api is a broader term that encompasses all types of apis that can be accessed over the internet, it includes rest,soap,xml-rpc etcc...
- the primary purpose of web api is to provide a paltform-independent interface that can beused by various clients.
- web api uses different protocols including http,https,tcp/ip to communicate between clients and server
- unlike rest api, it does not follow any specific architecture, instead it can be designed using any technology or architecture depending on the requirements
- one of the key feature of web api is that it provides a flexible interface that can be used by various clients.
- it allows developers to expose various functionalities of the application,  including crud operations, authenticaation,authorization etc

  ### When to use?
  - this web api is an excelent choice when building applications that require integration with different systems and technologies.
  - it provides a flexible interface that can be customized to meet the requirements of variosu clients including web,mobile and desktop applications
  - it is suitable for building applications that require authentication, authorization and security




  # SOAP API - simple object access protocol
  - is a messaging protocol used for excanging structured data between differnt application.
  - is a web based application programming interface that follows the soap messaging protocol.
  - the primary purpose of this soap api is to provide a standardized way to exchange data between applications, regardless of the platform or programming language used.
 -  it uses xml as the format for sending and receiving data, and it supports a wide range of data types, including text, numbers, dates and binary data
 -  it also supports multiple transport protocols, including http, smtp and ftp
 -  one of the essential feature of soap api is its ability to define a set of rules for exchanging messages between applications


### when to use?
- is an excellent choice when building applications that require a highly secure and reliable method of exchanging data between applications
- it is idea for enterprise-level applications that require complex data structures and business logic
- it is also suitable for applications that require advanced security features, such as digital signatures and encryption



# Summarize the differnce
| rest api | web api | soap api |
| ------ | ------ | ------- |
| - it follows rest architectural style | it doesnot allow any structure | it uses xml as its data format|
| - it uses http methods(get,post,put,delete) | it uses any protocol or tech | follows specific set of rules and protocols for communication|
| - it returns data in JSON or XML formal only | it uses any data format| soap has specific protocol, such as WSDL or UDDI|
| - it follows stateless client-server model | can be statefull or stateless | suitable for buidling enterprise-level apps|
| - it is suitable for simple application that require crud operations, adn real-time communicaiton | suitable for buiding complex applications that require integration with differnt system and technologies ||

  
