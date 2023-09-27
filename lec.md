# Lectures
## 3
### Storage Area Networks (SAN)
### Communication Cost
```
transmit time = distance/c + message_bits/bandwidth
c = speed of light (200 million meters/sec) with fibre optics
```
### Key DBMS Types
### ACID
### Significance of DBMS
### Module availability
### Object Oriented DB Systems(OODB) 
### NoSQL
### Deductive database systems (DDBS)

## 4
### Database Architectures
- centralised
- distributed
- www
- grid
- p2p
- cloud

### Performance
### Joins (simple, nested)
```
In the worst case, if there is enough memory only to hold one block of each table, the estimated cost is
nr * bs + br (bt)
nr + br (s)
---
br * bs + br (bt)
2br (s)
```
### Query Optimisation
Query Optimisation is about the right choices on a graph

## 5
### Cost-based Optimisation
### SQL & RA
Real life situation: Optimizers often use simple heuristics for very cheap queries, and perform exhaustive enumeration for more expensive queries
### Indexing
Indexing is important as it is "A key choice to make before optimization"
- Ordered indices
- Hash indices
- Primary index
- Secondary index
### B+trees
## 6
### B+trees
### Hash 

## 7
### Bitmap
### Quadtree
NN 
### K-d Tree
## 8
### R tree
### Transactions
## 9
### ACID in Transactions
### Codes
### Error Handling
## 10
### JDBC: Java Database Connectivity
### Flat Transactions
- Limitations: Any failure requires alot of unnecessary recomputation!!!
- Improvements: A savepoint is established by invoking the SAVE WORK function which causes the system to record the current state of processing.
### Nested Transactions
- Rules: commit, roll back, visibility
### Transaction Management: Monitors
The main function of a Transaction Processing Monitor is to integrate system components and manage resources so that transactions can run:

1. TP monitors manage the transfer of data between clients and servers

2. Breaks down applications or code into transactions and ensures that all the database(s) are updated properly

3. It also takes appropriate actions if any error occurs

### TP Monitors
- Terminal management
- Presentation service
- Context management
- Start/Restart
- Heterogeneity
- Control communications

### TP Process Structure I to III
## 11 - CC
### Concurrency Control
- Significance: Is needed to preserve consistency of the data for some number of tasks to work on the same data, i.e. concurrently. 
- Examples:
    Dekker's algorithm 
    OS supported primitives 
    Spin locks
### Semaphores 
## 12
### Semaphores 
### Deadlock
### Isolation
- Trade off between I & C
### Dependency
## 13
### Dependency Graph
- Transaction Equivalence
- Dependency and Isolation
- Wormholes

## 14
### S and X lock
### 2 Phase Locking (2PL)
- Serializability
### Strict two-phase locking (S2PL)
- Efficiency concern
### Degrees of Isolation
- Degree 3 (most strict)
- Degree 2
- Degree 1
- Degree 0 

先看是不是well formed，再看是不是2 phase

## 15
### Degrees of Isolation
### Granularity of Locks
```{figure} ./images/lock.png
---
height: 300px
name: lock
---
lock
```
### Two-version Locking
### Nested Transactions and Locking

## 16

### Optimistic Concurrency Control
Use data without locks, but with validations
- backward validations
- forward validations
### Snapshot Isolation
- Not the same thing as serializability
- Checks if what needs to be written is changed
- If not it is allowed to commit
- Things read are not checked
### Time-stamp-based Concurrency Control
```{note}
Timestamp ordering assigns orders for transactions based on time of commencement

Locking has some sort of order which is decided at object access time

When there are many updates two-phase locking is good as it has less aborts

Timestamp-based methods abort immediately which may be good some times

If there aren’t many updates an optimistic approach is better

… so there is no one winner for all DBMSs for all types of data/queries
```

### Networking Intro
mechanism design
1. Either all of the servers commit the transaction
2. Or all of them the transaction

> One of the servers becomes the coordinator. It must ensure the same outcome at all of the servers.


## 17 （学的不好
### Two-phase commit
- phase 1 - each participant votes. 
- phase 2 - the participants carry out the joint decision.
- voting phase
- completion phase
- participant and coordinator
- functions
    cancommit
    docommit
    doabort
    havecommitted
    getdecision
```{figure} ./images/2pc.png
---
height: 300px
name: 2pc
---
2pc
```
### Error Handling in Two-phase commit
- time-out actions in the 2PC is used
### Timestamp 
### Transactions with replicated data

## 18
### Fault Tolerance
### Disk failure rates
- Type of Error
    soft data
    seek
     maskable hard data
     un ...
     repair
### RAID
- RAID0 to RIAD6
###  Fault tolerance by voting
- Availability
    - Failvoting with 2 devices
            MTTF = 10/2 = 5 years (system fails with 1 device failure)

    - Failvoting with 3 devices
            MTTF = 10/3 for the first failure + 10/2 for 2nd failure = 8.3 years.
### Fault tolerance with repair
```
Probability of a particular module is not available
		 = MTTR/(MTTF+MTTR)   						
         ≅ MTTR/MTTF   if MTTF >> MTTR

```
### Supermodule
In general, a system with multiple hard disk drives is expected to function with only one working disk

$$
P = frac{1}{MTTF}
$$

## 19
### Recovery
### Data Storage
- Volatile storage
- Nonvolatile storage
- Stable storage
### Buffers
- Physical blocks 
- Buffer blocks 
### Data Access
### Cyclic Redundancy Check (CRC)
### Types of Recovery Systems
- log-based recovery
    1. Deferred database modification
    2. Immediate database modification
- shadow-paging
### Checkpoints

## 20 （之后学的也不好
### Checkpoints
### Concurrent Transactions
### Log Record Buffering
### Remote Backup Systems 
### Shadow-paging

## 21
### Data Warehousing
### OLAP（OnLine Analytical Processing）
### Data Cube
### Cross Tabulation with Hierarchy
### Information Retrieval Systems
### In Memory Databases

## 22
### Graph Databases
### Columnar Databases
### Limitation of Classical Commercial Systems in the era of Networking
### CAP
Any distributed database with shared data, can have at most two of the three desirable properties, C, A or P
### Eventual Consistency Variations
### BASE