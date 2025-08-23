---
{"dg-publish":true,"permalink":"/distributed-systems/module-6-advanced-topics-distributed-systems/","title":"Module 6 -- Advanced Topics -- Distributed Systems","tags":["Semester-6","Distributed-Systems"],"created":"2025-05-30T18:14:43.616+05:30"}
---

---
# Index

1. [[#Mobile Databases]]
2. [[#2. Distributed Object Management]]
3. [[#3. Multi-Databases]]

---
# Mobile Databases

https://www.geeksforgeeks.org/mobile-database/
## **Overview :**  

==A Mobile database is a database that can be connected to a mobile computing device over a mobile network (or wireless network). Here the client and the server have wireless connections. In today's world, mobile computing is growing very rapidly, and it is huge potential in the field of the database. It will be applicable on different-different devices like android based mobile databases, iOS based mobile databases, etc. Common examples of databases are Couch base Lite, Object Box, etc==.  
 
## **Features of Mobile database :**  

Here, we will discuss the features of the mobile database as follows.

- A cache is maintained to hold frequent and transactions so that they are not lost due to connection failure.
- As the use of laptops, mobile and PDAs is increasing to reside in the mobile system.
- Mobile databases are physically separate from the central database server.
- Mobile databases resided on mobile devices.
- Mobile databases are capable of communicating with a central database server or other mobile clients from remote sites.
- With the help of a mobile database, mobile users must be able to work without a wireless connection due to poor or even non-existent connections (disconnected).
- A mobile database is used to analyze and manipulate data on mobile devices.

## **Mobile Database typically involves three parties :**

1. **Fixed Hosts -**          
    It performs the transactions and data management functions with the help of database servers.  
     
2. **Mobiles Units -**       
    These are portable computers that move around a geographical region that includes the cellular network that these units use to communicate to base stations.  
     
3. **Base Stations -**       
    These are two-way radios installation in fixed locations, that pass communication with the mobile units to and from the fixed hosts.

## **Limitations :**  

Here, we will discuss the limitation of mobile databases as follows.

- It has Limited wireless bandwidth.
- In the mobile database, Wireless communication speed.
- It required Unlimited battery power to access.
- It is Less secured.
- It is Hard to make theft-proof.
---
# 2. Distributed Object Management

https://www.geeksforgeeks.org/distributed-object-systems/


==Distributed Object Management (DOM) refers to the management of objects in a distributed environment, typically within object-oriented databases or systems. It extends the principles of distributed databases to handle objects (which combine data and methods) rather than just relational data, focusing on how these objects are stored, accessed, and manipulated across multiple sites==.

- **What It Is**:  
    ==DOM involves distributing objects (e.g., instances of classes with attributes and methods) across nodes in a distributed system while ensuring transparency, consistency, and efficient access==. It’s ==often used in object-oriented database management systems (OODBMS)== or distributed frameworks.
    
- **Key Aspects of Distributed Object Management**:
    
    - **Object Distribution**:
        - **What It Is**: ==Objects are stored across multiple sites, similar to how data is distributed in a DDBS==.
          
        - **How It Works**: An object (e.g., a “Customer” object with attributes like name and balance, and methods like `updateBalance()`) can be partitioned or replicated across nodes.
            - **Partitioning**: ==Different parts of the object (or related objects) are stored on different nodes==.
            - **Replication**: ==Copies of the object are stored on multiple nodes for availability==.
              
        - **Example**: A “Customer” object with ID 101 might have its attributes stored on Node 1, while its related “Order” objects are on Node 2. A query accessing the customer’s orders needs to fetch data from both nodes.
          
    - **Object Replication**:
        - **What It Is**: ==Maintaining consistent copies of objects across multiple sites to improve availability and fault tolerance==.
          
        - **How It Works**: ==Similar to data replication in DDBSs, objects are replicated, and updates to one copy must be propagated to others to maintain consistency==.
            - Consistency models (e.g., strong consistency or eventual consistency) determine how updates are handled.
              
        - **Example**: A “Product” object is replicated on Nodes 1 and 2. If Node 1 updates the product’s price, the change must be propagated to Node 2 to avoid inconsistencies.
          
        - **Challenge**: Balancing consistency with performance—frequent updates across nodes can increase network overhead.
          
    - **Object Query Processing**:
        - **What It Is**: ==Executing queries on distributed objects while maintaining transparency (e309.g., location transparency, where the user doesn’t need to know where the object is stored)==.
          
        - **How It Works**:
            - ==Queries are decomposed into subqueries that are sent to the nodes where the objects reside==.
            - ==Results are combined and returned to the user, often using object references (e.g., pointers to objects on remote nodes).==
              
        - **Example**: A query to “find all orders for Customer 101” is sent to Node 1 (for the Customer object) and Node 2 (for the Order objects). The system joins the results and returns the list of orders.
          
        - **Transparency**: The user interacts with objects as if they were local, while the system handles the distributed nature behind the scenes.
          
- **Example Framework**:
    
    - **CORBA (Common Object Request Broker Architecture)**: A standard for distributed object management, allowing objects on different nodes (and even different platforms) to communicate.
        - How It Works: CORBA uses an Object Request Broker (ORB) to mediate between objects, enabling remote method invocation (e.g., calling a method on an object stored on another node).
        - Example: A Java application on Node 1 can invoke the updateBalance() method on a Customer object stored on Node 2 via CORBA.
          
- **Challenges**:
    
    - **Object Identity**: Each object has a unique identifier (OID) that must be consistent across nodes, even if the object is replicated or moved.
    - **Method Execution**: Deciding where to execute an object’s method—on the node where the object resides (to minimize data movement) or on the requesting node (which may require transferring the object).
    - **Consistency**: Ensuring that replicated objects remain consistent, especially when methods modify object state.
    - **Performance**: Remote method calls and object access over a network can introduce latency compared to local execution.
      
- **Use Case**:  
    Distributed Object Management is common in systems that use object-oriented databases, like in enterprise applications (e.g., a distributed e-commerce system where Customer, Order, and Product objects are managed across multiple servers). It’s also used in middleware frameworks like CORBA or Java RMI (Remote Method Invocation) for distributed computing.

---
## Architecture of Distributed Object Systems

The architecture of Distributed Object Systems typically involves several key layers:

- ***Client Layer:*** This is where the user interacts with the system. Clients can be anything from web browsers to desktop applications that initiate requests to access distributed objects.
- ***Middleware Layer:*** Middleware serves as an intermediary that facilitates communication between clients and distributed objects. It handles object location, message routing, and data serialization.
- ***Object Layer:*** This layer consists of the actual distributed objects that contain the business logic. These objects are often implemented as remote objects, which are instantiated on different servers.
- ***Database Layer:*** Many distributed object systems rely on a back-end database to store persistent data. This layer manages data integrity and transactions across distributed nodes.
- ***Network Layer:*** The network layer provides the necessary communication infrastructure, including protocols and services for reliable data transmission.

---
## Object Management

Managing objects in a distributed environment presents unique challenges. Key aspects include:

- ***Object Creation and Destruction:*** Distributed objects can be created and destroyed dynamically. Object factories can be used to manage object lifecycle and ensure resources are appropriately allocated and released.
- ***Object Persistence:*** Distributed objects may need to maintain state over time. Object databases or serialization mechanisms can be employed to store object states persistently.
- ***Object Discovery:*** Object discovery mechanisms help clients locate objects across a distributed environment. This can involve naming services or registry services that track object locations.
- ***Object Versioning***: Managing different versions of an object is crucial for compatibility. Versioning strategies ensure that clients can interact with the correct object version without disruption.

---
## Security in Distributed Object Systems

Security is a paramount concern in Distributed Object Systems, where data travels over networks that can be susceptible to attacks. Key security measures include:

- ***Authentication:*** Ensuring that clients and objects are who they claim to be is vital. Mechanisms such as tokens, passwords, and public key infrastructure (PKI) can be employed.
- ***Authorization:*** Once authenticated, clients must be authorized to perform specific actions on objects. Role-based access control (RBAC) is a common strategy for managing permissions.
- ***Encryption:*** Data transmitted over the network should be encrypted to protect against eavesdropping. Protocols like TLS (Transport Layer Security) are widely used.
- ***Integrity Checks:*** Ensuring that data has not been altered in transit is crucial. Checksums and digital signatures can be used to validate data integrity.

---
## Communication Protocols in Distributed Object Systems

Effective communication is essential for the functionality of Distributed Object Systems. Various protocols are utilized to facilitate object communication:

- ***Remote Method Invocation (RMI):*** RMI allows a program to invoke methods on an object located in another JVM (Java Virtual Machine). It abstracts the complexity of network communication, making remote calls appear local.
- ***Common Object Request Broker Architecture (CORBA):*** CORBA is a standard defined by the Object Management Group (OMG) that enables communication between objects in different programming languages. It uses Interface Definition Language (IDL) to define object interfaces.
- ***Web Services:*** Web services utilize standard protocols like HTTP and XML (SOAP and REST) to enable communication between distributed objects over the web. They are widely used for interoperability between different systems.
- ***Message-Oriented Middleware (MOM):*** MOM facilitates asynchronous communication between distributed objects. It uses message queues to send and receive messages, decoupling the sender and receiver.
- ***gRPC:*** gRPC is an open-source RPC framework that uses HTTP/2 for transport and Protocol Buffers for serialization, allowing for efficient communication between distributed components.

---
### Key Considerations

- **Relation to DDBSs**: DOM applies distributed database principles (e.g., replication, query processing) to objects instead of relational tables. It’s a natural fit for object-oriented systems but adds complexity due to the need to manage both data (attributes) and behavior (methods).
- **Modern Relevance**: While traditional DOM frameworks like CORBA are less common today, the concepts are still relevant in modern distributed systems, such as microservices architectures where objects (or their equivalents, like JSON data) are managed across services.

---
# 3. Multi-Databases

==Multi-databases (also known as multidatabase systems) involve integrating multiple independent databases into a single, unified system, allowing them to operate as a cohesive unit while retaining their autonomy. This is often used in scenarios where different organizations or departments have their own databases but need to share data or perform global queries==.

- **What It Is**:  
    ==A multi-database system combines several autonomous databases, each with its own schema, data model, and management system, into a federated system that appears as a single database to users.== Each database retains its independence but participates in a global framework.
    
- **Key Concepts**:
    
    - **Federated Databases**:
        - **What It Is**: A collection of autonomous databases that are integrated to support global queries and transactions, while each database maintains its local control.
          
        - **How It Works**: A global schema (a unified view) is created to map the schemas of the individual databases, allowing users to query the system as if it were a single database.
          
            - Local databases (called component databases) manage their own data and operations.
            - A federation layer handles query decomposition, translation, and result integration across the databases.
              
        - **Example**: A university has separate databases for its library, student records, and payroll systems. A federated system allows a query like “find all students who borrowed books and their payment status” by accessing all three databases transparently.
          
    - **Challenges**:
      
        - **Schema Integration**:
            - Different databases may use different schemas, data models (e.g., relational, object-oriented), or naming conventions.
              
            - Example: One database might store “`StudentID`” as “SID” (integer), while another uses “`Stu_ID`” (string), requiring mapping and transformation.
              
            - Solution: A global schema resolves these differences by defining a unified view, often using wrappers or mediators to translate between local and global schemas.
        - **Query Processing Across Heterogeneous Databases**:
            - Queries must be decomposed into subqueries for each local database, executed, and then combined.
              
            - Challenges Include:
                - Heterogeneity in query languages (e.g., SQL vs. NoSQL).
                - Differences in performance and capabilities of local systems.
                - Network delays when accessing remote databases.
                  
            - Example: A global query “find all employees with overdue library books” requires querying the payroll database for employee data and the library database for book records, then joining the results.
              
        - **Autonomy**: Each database retains control over its data and operations, which can lead to conflicts (e.g., one database might refuse to share certain data).
          
        - **Consistency**: Ensuring consistency across databases is hard, especially if they update independently.
    - **Solutions**:
      
        - **Global Schema**: A unified schema that maps the local schemas, providing a consistent view for global queries.
            - Example: The global schema might define a “Person” entity that maps to “Employee” in the payroll database and “User” in the library database.
        - **Middleware**: A software layer (e.g., a mediator or wrapper) that handles communication, query translation, and data integration between the databases.
            - Wrappers convert local data and queries into a format compatible with the global system.
            - Mediators coordinate query execution and result integration.
        - **Query Optimization**: The system optimizes global queries by considering the capabilities and performance of each local database, minimizing data transfer and processing time.
        - **Transaction Management**: Using distributed transaction protocols (like 2PC, which you’re familiar with) to ensure atomicity across databases, though autonomy can make this challenging.
          
- **Use Case**:  
    Multi-databases are used in scenarios where organizations need to integrate existing databases without merging them into a single system. Examples include:
    
    - Healthcare systems integrating patient records from multiple hospitals.
    - Government agencies sharing data across departments (e.g., tax, health, and education).
    - Corporate mergers where each company has its own database but needs to operate as a single entity.

---
### Key Considerations

- **Relation to DDBSs**: Multi-databases are a type of distributed database system, but they emphasize autonomy of the local databases, unlike a traditional DDBS where the system is designed as a single, cohesive unit from the start.
- **Modern Relevance**: Concepts from multi-databases are used in modern data integration platforms, like data lakes or enterprise data warehouses, where heterogeneous data sources (e.g., SQL databases, NoSQL stores, and cloud storage) are queried as a unified system.

---
