# Comparisons
## Key DBMS Types
|   | Definition | Example | Pros | Cons |
|---|---|---|---|---|
| Simple File | A plain text file, each line holds one record, with fields separated by delimiters. | A text file on the desktop recording account information separated by tabs. | Fast | Less reliable in terms of concurrency, hard to maintain |
| Relational DBMS (RDBMS) | A collection of tables (relations) consisting of rows and columns, typically using SQL. | MySQL, Microsoft SQL Server | Reliable, can handle complex data, fast | Expensive, require lots of physical storage, can be slow with many tables |
| Object-Oriented DBMS (OODBMS) | Data stored in the form of 'objects' directly. | Used in applications requiring high performance, calculations, and faster results, such as 3D modeling and real-time systems. | Reliable, can handle complex data | Slow, rarely used in real life |
| NoSQL DBMS | An approach to database design enabling storage and querying of data outside traditional structures found in relational databases. | Pure document databases, key-value stores, wide-column databases, and graph databases. | Reliable, fast, easy implementation | Lack of standardisation, might require cross-platform support |


## Types of NoSQL Databases

|   | Definition | Example | Pros | Cons |
|---|---|---|---|---|
| Key-Value | Store data collection of keys and simple pairs. Suitable for DB without complex relation structures. | - | Useful because many applications do not require expressive functionality for transactions. | - |
| Document-Based | Extension of key-value; key-documents allowing complex operations. Scales quickly and allows fast insert & delete operations. | MongoDB | Allows complex operations, scales quickly, allows fast insert & delete operations. | - |
| Column-Based | Data is isolated, only part of the information is stored, each row only stores one data. | Amazon Red Shift | Fast, data is isolated. | - |
| Graph Database | Purpose-built to store and navigate relationships. Good at dealing with intensive data relations. | Netflix | Good at dealing with intensive data relations. Performance does not decrease as data increases. Easy to insert, delete, and update. Can change DB size according to business size. | Hard to find support, no standard query language. |

## Different Types of Database Architecture
|   | Definition | Pros | Cons |
|---|---|---|---|
| Centralised | Data stored in one location | Suitable for simple application, easy to manage | Access speed is limited by network speed, potential for data loss in case of hardware failure without fault-tolerant setup |
| Distributed | Data is distributed across several nodes in different locations | Scalable, can be built across different locations, quicker for accessing local data | Crash recovery can be difficult, potential for data inconsistency |
| World Wide Web (WWW) | Data is stored and shared globally | Convenient for accessing and sharing data, data ownership is distributed, data is stored worldwide | Security issues, no guarantee of availability or consistency |
| Grid Computing and Database | Similar to distributed systems, but with different DB management methods | Flexible, scalable | May have problems with transactions |
| Peer to Peer (P2P) | Similar to grid, but with different DB management methods. Every node has the same role and job, nodes are free to join and leave | Suitable when nodes cannot be planned in advance | Difficult to design transactions |
| Cloud Database | User pays for the service as they go | On-demand resources, cost-effective, maintenance is done externally by the cloud providers | Privacy issues, confidentiality issues |

## SSD & HDD
|   | SSD | HDD |
|---|---|---|
| Speed | Generally faster, quicker data access and boot times | Slower compared to SSD |
| Durability | No moving parts, so more resistant to physical shock | Has moving parts, so more vulnerable to physical shock |
| Noise | No noise as there are no moving parts | Can produce some noise due to moving parts |
| Lifespan | Limited number of write cycles, but can last a long time with normal usage | Lifespan depends on mechanical wear, can be longer with light usage |
| Price | More expensive per gigabyte | Less expensive per gigabyte |
| Capacity | Typically smaller capacities | Larger capacities more common |

## ACID & BASE
|             | ACID                                                            | BASE                                                             |
|-------------|-----------------------------------------------------------------|------------------------------------------------------------------|
| Definition  | Atomicity, Consistency, Isolation, Durability                    | Basically Available, Soft state, Eventually consistent            |
| Advantages  | Strong consistency and integrity. Ideal for critical applications| Better performance, highly available, scalable. Ideal for large data |
| Disadvantages| May negatively affect performance. Not ideal for distributed systems | Lack of strong consistency. More complex debugging and testing |
