# Tutorial Key Points
## Tut1
### hard disk drive (HDD)
- seek time delay
- rotation time delay
- disk access time
```{math}
    disk\_access\_time = seek\_time + rotation\_time + \frac{transfer\_length}{bandwidth}
```
### solid state drive (SSD)
- disk access time
```{math}
    disk\_access\_time = \frac{transfer\_length}{bandwidth}
```
There is no seek time and rotation time, as SSD don't have the mechanical part. 
```{Note}
Advantage of SSD: doesn't have a mechanical part, so it's faster.
```
### Effective memory access time
$$EA = HC + (1-H)M$$
C = cache access time

M = memory access time

### Effective memory access time
$$EA = HB * BC + (1- HB)*D$$
HB = hit ratio of the disk buffer

BC = buffer access time

D = disk access time

### Pros and Con of database type
RDBs, Simple File-based, OO

| Storage Type     | Pros                                  | Cons                                            |
| ---------------- | ------------------------------------- | ----------------------------------------------- |
| Simple File      | Fast                                  | Less reliable, hard to maintain                 |
| RDBS             | Very reliable, fast                   | Can be slow for some applications               |
| Object Oriented  | Reliable, can handle complex data     | Slow, not much development in real life         |
| NoSQL            | Flexible, scale linearly              | Can cause consistency issues                    |

### No SQL DB
```{note}
simple key-value pairs: shopping cart database in an e-commerce site.

non-uniformed-structure:  news articles db

column-based 

graph databases: spatial data.

```
> 
    • Applications for key-value databases: Suitable if the dataset does not need a complex relational table type of structure but can be expressed with simple key-value pairs. The simple structure allows faster insertion and search and scales quickly. For example, a shopping cart database in an e-commerce site.

    • Applications for document storages: Well suited when different kinds of documents do not always have the same structure/sections. For example – a database of news articles.

    • Applications for column-based NoSQL databases: They are used in data analysis applications/tasks.

    • Applications for graph databases : Well suited for storing connection data such as social network connections and



---

## Tut2

### DB Architecture Pros and Cons
| Database Type     | Pros                                                        | Cons                                                   |
| ----------------- | ----------------------------------------------------------- | ------------------------------------------------------ |
| Centralised       | Suitable for simple applications, easy to manage.           | May not scale well.                                    |
| Distributed       | Scalable, suitable for large applications and applications that need data access from different physical locations. | System administration and crash recovery are difficult. These systems usually have some data inconsistency issues. |
| WWW               | Very convenient to access and share data.                   | Has security issues, no guarantee on availability or consistency. Extreme levels of administration issues. Ultimately did not take off because of this reason. |
| Grid              | High processing capability as well as access at different locations. | Similar issues to distributed databases. Less used nowadays, very similar to distributed systems with administration done locally by each owner. |
| P2P               | Suitable when the nodes of the network cannot be planned in advance, or some may leave and join frequently. | Difficult to design transaction models. Applications are usually limited to simple file sharing. |
| Cloud-based Databases | On-demand resources, **cost-effective**, maintenance done externally by the cloud provider. | Has some privacy and confidentiality issues among others – but most trusted providers can address any issues emerging on this type relatively easily, e.g., Amazon, etc. |

*Cloud storage allows for data to be stored across multiple servers in data centers, making it easier to **scale horizontally** as the number of users grows. This type of architecture also provides better **reliability** and **fault tolerance**.*

*Unlike the previous scenario, if data is transferred and stored in a 3rd party storage like the cloud, the security is not in the hands of FriendBook (including encryption guarantee, data discloser agreement, etc.). Hence, having the setup of their own distributed database (as they are located across many cities with many users across the globe) is a more suitable solution.* 

### ACID

- Atomicity: A transaction’s changes to the state (Database) are atomic implying either all actions happen or none happen.
- Consistency: Transaction are a correct transformation of the state. Actions taken as a whole by a transaction do not violate the integrity of the state. That is we are assuming transactions are correct programs. 
- Isolation: Even when several transactions are executed simultaneously, it appears to each transaction T that others executed either happen before T or after T but not at the same time. Concurrent execution of transactions should not violate consistency of data.
- Durability: State changes committed by a transaction survive failures.


### heuristics or enumerating


```
# Scenario A: Given a table with 10 million tuples, run the following query:
SELECT customer
            FROM Table
            WHERE spend BETWEEN 100 AND 200
            AND birth_year> 2000;
```

```
 Scenario B: Given 5 tables with 1000 tuples in each table, run a query:
               SELECT T1.name, T2.salary, T3.qualification, T4.phone, T5.leader
               FROM Table1 T1
                   INNER JOIN Table2 T2 ON T2.id = T1.id
                   INNER JOIN Table3 T3 ON T3.id = T1.id
                   INNER JOIN Table4 T4 ON T4.id = T1.id
                   INNER JOIN Table5 T5 ON T5.department = T1.department
               WHERE T1.age > 50;

```
```{admonition} which query optimizer should be used for the 2 scenarios?
:class: dropdown
A: heuristic  (as the query is simple)

B: enumerating (as the query is complex)
```

### Simple & Nested Loop Join
Why is nested loop join more efficient?
> After reiterating the examples/calculations, we see the latter one is most efficient because each block in the inner relation
is read once for each block in the outer relation (instead of once for each tuple in the outer relation).

---

## Tut3
- Hash index.
- B+ tree index.
- R-tree
- Quad tree
- Bitmap

### Max height of a B+ Tree
$$⌈log⌈n/2⌉(K)⌉$$

### Bitmap conversion
Perryridge, Brooklyn, Jonestown, Brooklyn, Perryridge

- Perryridge : 10001
- Brooklyn: 01010
- Jonestown: 00100

### B+ tree -  Search a term
Algorithm is on Slide 2 Lecture 6.

### R tree - 1st nearest neighbor
To Find the nearest neighbor, we want to loop through all the point ih the nearest block, if a point is in overlapped sections, we want to investigate the all sections. 

---

## Tut4
### Isolation property application
- isolation improves efficiency (comparing to 1 by 1)
- isolation guarantees concurrency

Discuss why the isolation property of ACID properties will apply to both an Online shopping platform as well as an Online banking system despite that they are different applications dealing with different data.
> Both types of systems may need to serve a large number of customers at any given time. 
For achieving consistency, both systems require that a transaction does not use the values that have 
been modified by another uncommitted transaction. A naïve approach to achieve this is handling one 
customer at a time. But the efficiency of the service would be extremely low with this approach. 
Therefore, the systems should allow different transactions to run concurrently. At the same time, 
the changes to the data are made as if the transactions run on a serial schedule, i.e., a transaction 
runs as if it is the only transaction in the system and does not become aware of other concurrent 
transactions which is the objective of isolation. Isolation helps with achieving a high level of efficiency 
while maintaining the consistency of the data that is manipulated.

### Roll back
- parent roll back

    Parent itself rolls back + all of its children roll back
- children roll back

    Only the children itself rolls back

### TP monitoring - why only using single process is not good
> One error in the process can impact all the transactions. This could lead to poor performance as well as monitors of
different transactions cannot be distributed either.

### Flat transaction - cons
- time consuming
- error prone
> The customer table here could be a large table with millions of customers. This means this transaction can potentially be doing a lot of work during its execution and take a long time. Any failure in this transaction’s execution would mean a lot of work lost. So better not to have this transaction as a flat transaction.

### Finish drawing of a quad tree
- split each cell as a 田, make sure only one point in each cell

---

## Tut5
### Why not 100% isolation (AKA isolation vs concurrency)
- optimise performance and resource utilisation
- optimise throughput (system efficiency)
- promote user experience (by avoiding long waiting time)

```{admonition} Explanation in details
:class: dropdown
- Performance optimization: 

    Allowing concurrent execution of transactions can improve system performance by utilizing idle resources and reducing overall execution time. Strict isolation would require transactions to run sequentially, leading to potential resource idle time and slower overall performance.

- Resource utilization: 

    Running transactions concurrently allows for better utilization of system resources, such as CPU, memory, and disk access. If transactions are strictly isolated, idle resources may not be effectively utilized, resulting in underutilization and inefficient resource allocation.

- Throughput and responsiveness: 

    Concurrent execution allows multiple transactions to make progress simultaneously, leading to higher throughput and better responsiveness. Strict isolation can result in blocking or waiting for other transactions to complete, leading to lower throughput and longer response times.

- User experience:

    Strict isolation may lead to long transaction delays, especially if there are long-running transactions in the system. This can impact user experience and customer satisfaction, especially in scenarios where timely completion of transactions is crucial.

```

### Lock
simple lock is not enough if it is not well formed. Well formed means that the write should be within lock. 

- degree3: X, S 2 phase
- degree2: X 2 phase, S lock can be non-2-phase, read is in s lock 
- degree1: X 2 phase, read is in not in s lock
- degree0: X, S non-2 phase

---

## Tut6

### Semaphore
### deadlock
### dependency graph

## Tut7
### dependency graph

## Tut8
## Tut9