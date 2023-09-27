# Past Exam
## 2021

### Q1 - RAID
Which of the following RAID settings has the equal number of write operations on
average among all the disks?
- RAID 4 with 3 disks
- RAID 4 with 5 disks
- RAID 3 with 3 disks
- RAID 1 with 3 disks
```{note}
:class: dropdown
equal number of write operations => mirror => RAID 1
```
### Q2 - CAP
In a distributed database with shared data, the following options show the desired
properties in pairs. Which one of these pairs cannot be achieved together at the
same time?

- Consistency and partition tolerance
- Availability and consistency
- Availability and partition tolerance

```{note}
:class: dropdown
key is Consistency, so answer must contain Consistency
```
### Q3 - DBMS Types
Weather service Australia has installed multiple sensors in Melbourne with a small
computing device in them. Each computing devices store and manage the data of
its own sensor. When the sensors record any new data, they connect with the
other nearby sensors in an ad-hoc network, share those data, and then
disconnect. Which of the following database architecture is the most suitable
choice for this scenario?

- P2P databases
- Cloud storage
- Centralised database
- Distributed database


```{note}
:class: dropdown
**manage the data of its own sensor** => P2P
```
### Q4 - failfast
Which system is expected to be available more (e.g., expected to function for
longer) than the other system? (i) System A with 5 devices on failfast (ii) System B
with 5 devices as a supermodule

- System B
- System A
- Both system A and system B have the same availability

```{note}
:class: dropdown
 > Failfast systems are designed to immediately report any failure or issue as soon as it occurs. In other words, if a component in this system fails, the entire system will stop working. This can be beneficial for diagnosing and fixing issues as they occur, but it also means that the availability of the system could be lower, because it will stop functioning as soon as a single component fails.

=> System B
```
### Q5 - SSD & HDD
John needs to buy a new computer. He usually uses his computer to play online
games, listen to music, watch movies, work on word documents for his studies,
and browse social networks. He cannot decide which of the following options of hardware will be suitable for him. Please explain the advantages and disadvantages of each option for him. Assume both options cost the same.

Option 1: 250 GB solid state drive, 8 MB cache

Option 2: 500 GB hard disk drive, 32 MB cache
```{note}


|            | Option 1: 250 GB SSD, 8 MB Cache | Option 2: 500 GB HDD, 32 MB Cache |
|------------|----------------------------------|-----------------------------------|
| **Advantages** |   |   |
| Speed       | Very fast (quick load times, fast booting)  | Slower than SSD  |
| Durability  | High (no moving parts)            | Lower (has moving parts) |
| Noise       | Silent operation                  | Noise due to moving parts |
| Storage Capacity | Lower (250 GB)                  | Higher (500 GB) |
| Cache Size  | Lower (8 MB)                      | Higher (32 MB) |
| **Disadvantages** |  |  |
| Storage Capacity | May not be sufficient for large files | More than enough for most users |
| Speed       | -                                 | Could be slow for demanding tasks |
| Durability  | -                                 | Vulnerable to physical shocks |
| Noise       | -                                 | Generates more noise and heat |
| Cache Size  | Smaller cache may slow data transfers | Larger cache can speed up data transfers |
```

### Q6 - Nested transaction
In a nested transaction, a sub-transaction can commit, but the actual commit will
not take place until all its ancestor transactions commit. Then why is a nested
transaction still useful?
```{note}
:class: dropdown
Nested transactions are useful for:

0. **Reuse**: They can be written as a function.
1. **Modularity**: They allow structuring large transactions into manageable units, improving organization of code.
2. **Error Handling**: If a sub-transaction fails, it can be rolled back without affecting the parent transaction, improving error isolation and recovery.
3. **Concurrency**: They can potentially improve performance by allowing different sub-transactions to execute in parallel, depending on the database system.
4. **Resource Management**: They can reduce database contention by committing earlier to release locks, improving overall system performance.
```

### Q7 - Semaphore (binary and counting)
In a database, the table ‘student_records’ is very frequently accessed by many
concurrent transactions and processes, for both reading and writing purposes. In
the same database, the table ‘classroom_records’ is rarely accessed. What type
of semaphore should be used for each of these two database tables? Are these
semaphores of the same type for both tables? Why or why not?

```{note}
:class: dropdown
- counting semaphore, as the data is not a single data. Yes, the same as both of them are table.

There are 2 types of semaphore, binary and counting. Binary semaphore is used to control access to a single resource. Single resource is something really simple: i = 1. A table is not a single resource.
```

### Q8 - Deadlocks
Many systems employ a simple strategy to handle deadlocks - they just allow a
transaction to wait for certain maximum time on a lock, and then force it to
rollback. Why is this strategy used by most systems? What are the benefits of this
strategy over the other possible strategies to handle deadlocks?

```{note}
:class: dropdown
- strategy

    > deadlock detection and resolution: setting a maximum wait time on a lock and forcing a rollback if that time is exceeded.

- reasons for application

    1. **Simplicity:** It is a straightforward and relatively easy strategy to implement compared to others, like deadlock prevention or avoidance. A timer just needs to be associated with each lock request.

    2. **Performance:** It has minimal impact on system performance under normal conditions (i.e., when there are no deadlocks), because transactions do not need to constantly check for potential deadlocks.

    3. **Resource Utilization:** It allows resources to be utilized more fully and efficiently, because transactions do not need to prove in advance that they will not cause a deadlock (which can be conservative and leave resources unused).

    4. **Effectiveness:** When a deadlock does occur, it can be resolved quickly by rolling back one or more of the transactions involved, freeing up all the resources it was holding.

    Compared to other strategies, like deadlock prevention or avoidance:

    1. **Deadlock prevention** typically requires a system to be overly conservative by strictly ordering resource requests or by requiring transactions to claim all their resources upfront, both of which can reduce concurrency and system throughput. The forced wait and rollback strategy allows for higher resource utilization.

    2. **Deadlock avoidance** requires a system to have complete and accurate knowledge of future resource requests, which is not possible in most real-world systems. The forced wait and rollback strategy only requires knowledge about currently held and requested locks, making it more practical to implement.

    In short, the forced wait and rollback strategy provides a balance between simplicity of implementation, system performance, resource utilization, and effectiveness in resolving deadlocks, making it a popular choice for many systems.
```

### Q9 - Isolation Degrees
Degree 2 isolation may have ‘non-repeatable read’ type of concurrency problem. What are the benefits of using Degree 2 isolation then? Can you give an example application scenario where a Degree 2 isolation can be useful over a strict Degree 3 isolation.

```{notes}
:class: dropdown

benefits:
    1. increased concurrency: allow unrepeatable reads (as it only lock data that is being written).
    2. prevent lost update and dirty read (as it doesn't read uncommitted data from another transaction, ensuring a higher level of data consistency. )

example:
    consider example that value accessibility > consistency
    high-demand online news website: An application scenario where Degree 2 isolation can be useful over strict Degree 3 (Repeatable Read or Serializable) isolation would be a high-traffic online news website. On such a website, most users are simply reading articles, and it's more important to serve a large number of read requests quickly than to ensure absolute consistency of data. In this case, the risk of a non-repeatable read (e.g., the article changes slightly between two reads during the same transaction) is an acceptable trade-off for the benefit of being able to serve more users concurrently.
```

### Q10 - Lock Table
The following transactions are issued in a system at the same time. Answer for both scenarios.

(i) Scenario 1: When the value of the variable some_input is 3, which of the following transactions can run concurrently from the beginning till commit (that is, all operations and locks are compatible to run concurrently with another one) and which ones need to be delayed? Please give explanation for the delayed transactions.

(ii) Scenario 2: When the value of the variable some_input is 1, which of the following transactions can run concurrently from the beginning till commit (that is, all operations and locks are compatible to run concurrently with another one) and which ones need to be delayed? Please give explanation for the delayed transactions.


```{figure} ./images/Q10.png
---
height: 300px
name: Q10
---
Q10
```

```{figure} ./images/lock.png
---
height: 300px
name: lock
---
lock
```

```{note}
:class: dropdown
Use the above table, we can see that, is the current lock is IS, we can grant an S lock. But if the current lock is IX, we can't grant an X lock. 

(i) T1, T2 can. T3 delayed.

S - IS - S (✅)
IS - S - S (✅)


(ii) T1, T2 can. T2, T3 can
```
### Q11 - Transaction Recovery
We have a simplified log at the time of a system crash. Assume that there is no log record before the checkpoint. The format of a log record is (LSN, Operation Details).

(00, begin checkpoint)

(05, end checkpoint)

(10, T1 write Page1)

(20, T2 write Page2)

(30, T1 write Page5)

(40, T2 commit)

(45, T2 end)

(50, T3 write Page5)

(60, T1 abort)

(70, CLR undo T1 LSN 30)

(80, CLR undo T1 LSN 10)

(90, T1 end)

CRASH
The system recovery consists of three phases: analysis, redo and undo. Please answer each of the following questions.

A. What information will be in the dirty page table after the analysis phase (write
as a list of the format (Page id, LSN))?

(50, page5): because T3 write Page5 whilst T1 hasn't commit

B. If the pageLSN of Page5 stored in the database is found as 30, then what will
be the order of the LSNs to be redone in the Redo phase? Assume that all the
necessary pages are in the dirty page table, all LSNs in the log are greater than or
equal to the corresponding page’s recLSN, and all LSNs in the log are greater
than the corresponding page’s pageLSN (except for Page5).

C. What is the order of the LSNs to undo in the Undo phase?

### Q12 - Error Handling RAID
A company needs to store some sensitive medical records on disk. It is very
critical that no error occurs, and no data is lost while storing the records. They can
use multiple disks for the storage purpose if necessary. What strategies can they
use to minimize the chance of any error while writing the data on disk? What
strategies can they use to detect whether any error occurred or not? How can they
still use the data if an error is detected? You do not need to describe the detailed
steps of the strategies.

- RAID (1,5)
- partition
- parity


## Semester 1, 2022, Final Exam

### Question 1: DBMS Type
[4 Marks]

In one paragraph, compare Relational DB systems with Object Oriented DB Systems.

```{note}
:class: dropdown
- Simple file(s)

    As a plain text file. Each line holds one record, with fields separated by delimiters (e.g., commas or tabs).
    
- RDBS

    As a collection of tables (relations) consisting of rows and column. A primary key is used to uniquely identify each row.
- Object oriented

    Data stored in the form of 'objects' directly
- No-sql

    Non relational-database modelled other than the tabular relations. Covers a wide range of emerging databases. 
```


### Question 2: Index Comparison
[6 Marks]

We have seen the B+tree concept for indexing in class. These trees are deemed as an improvement over binary trees with their large fan out e.g., in the range of 100s.

 i) What is the benefit of making such a decision with fan outs, especially in the context of DBMSs? Briefly explain. 

ii) What are the benefits and disadvantages of using a B+tree in
comparison to using hashing? Briefly explain.
```{note}
:class: dropdown
i) The large fan-out of B+ trees can significantly reduce the height of the tree, which is beneficial for database management systems (DBMSs) because it minimizes the number of disk I/O operations required to locate a record. The larger the fan-out, the more keys can be stored in each node, reducing the number of levels in the tree. This can make searching for data more efficient, as disk access is often a major performance bottleneck in DBMSs.

ii)

**Benefits of using a B+ tree over hashing:**

B+ trees maintain data in a sorted order, which allows for efficient range queries. Hashing, on the other hand, does not maintain any order, making range queries inefficient.

B+ trees can handle situations where several keys hash to the same hash value (collisions), while hash-based structures may require special handling for such cases.

B+ trees are more dynamic and can easily grow and shrink as elements are inserted or deleted. Hashing typically requires rehashing, which can be computationally expensive, to adjust the number of buckets when the number of elements changes significantly.

**Disadvantages of using a B+ tree over hashing:**

Hashing can often provide faster access times for individual records, as a perfect hash function would provide a constant time complexity (O(1)) for search operations. In contrast, B+ trees have a time complexity of O(log n).

Hashing may require less storage space as there is no need to store pointers to child nodes, as in the case of B+ trees.

While B+ trees handle collisions gracefully, they have an overhead of balancing the tree after insertions and deletions to maintain the tree's properties. This isn't required in hashing.
```
```{admonition} fan-out

In the context of tree data structures, like B+ trees, the term "fan-out" refers to the maximum number of children that a node can have. Essentially, it's a measure of the "branching factor" of the tree.

For example, in a binary tree, the fan-out is 2 because each node can have at most two children. In a B+ tree, the fan-out is typically much larger. A B+ tree with a fan-out of 100, for instance, means that each node in the tree could have up to 100 children.

Increasing the fan-out decreases the height of the tree, which can make traversing the tree more efficient, especially in cases where reading from a node is a costly operation, such as in a disk-based storage system like a database.

```
### Question 3: Dependency Graph
 [6 Marks]

Given the following transaction history h we are told that k, l, m, n, o, and p are
transactions, and operations are Read and Write operations which are labeled as R and W,
and operations are done on the objects labeled as a, b, c, d, e:
h = < (k,R,a),(m,W,a),(m,W,b),(n,R,b),(k,W,c),(l,W,e),(o,R,c),(o,R,d), (p,W,d) >

Please find the DEP(h) and draw as a simple graph version as well. Then using the
concept of wormholes explain whether this history is equal to a serial history or not, i.e.,
if this history is not equal to a serial history then give a wormhole example, and if it is
then give a serial execution of these transactions that this history is equal to. Briefly
explain your steps with sentences while answering this question.

```{note}
There is no wormholes as there is no cycle. Hence the history is equal to a serial history: <k,a,m>...
```
### Question 4: Cascading Aborts
[5 Marks]

What is cascading aborts? Does two-phase locking address them? If it does, explain
how, but if it does not, then give a locking-based strategy that may address them, and
then explain briefly how that strategy that you gave will address them.

```{note}
:class: dropdown

1. A situation in which the abort of one transaction forces the abort of another transaction to prevent the second transaction from reading invalid (uncommitted) data.

2. Also called "cascading rollback".

3. 2PL + Cascading aborts => S2PL

4. two-phase locking doesn't address them (?), but S2PL address them. 

```
### Question 5: K-d Tree 
[4 Marks]

Given the k-d tree below with point data, where black labeled dots represent spatial
coordinate data, and the rectangular area is divided into regions with the division order
given with numbers: draw the associated k-d tree as a tree structure with leaves labeled as
the data labels given below. Assume left subarea of a division goes to a left subtree, and
lower subarea of a division also goes to a left subtree. The figure for the k-tree follows:
```{figure} ./images/kdtree.png
---
height: 300px
name: kdtree
---
kdtree
```

answer: see appendix

### Question 6: Cyclic Redundancy Check
[5 Marks]

We want to use the Cyclic Redundancy Check method for data storage as a means to
deal with errors. Please compute the additional bits that we need to store with the original
data, given the following information. Show your steps and calculations. Original data is
11100001 and your divisor polynomial is x4 + x2 + x + 1.

answer: see appendix
### Question 7: ACID and BASE
[4 Marks]

Compare ACID and BASE properties; what do they aim each; what are their
differences, and advantages or disadvantages if a DBMS designer follows one or the
other set. Briefly explain.

1. Atomicity:
A transaction’s changes to the state (Database) are atomic implying either all actions happen or none happen.
2. Consistency:
The transaction is a correct transformation of the state. Actions taken as
a whole by a transaction do not violate the integrity of the state. That is
we are assuming transactions are correct programs.
3. Isolation:
Even when several transactions are executed simultaneously, it
appears to each transaction T that others executed either happen
before T or after T but not at the same time. The concurrent execution
of transactions should not violate the consistency of data.
4. Durability:
State changes committed by a transaction survive failures

### Question 8: Shadow paging
[4 Marks]

Shadow paging is a mechanism one can use in database recovery. It is said that it is an
approach where almost no recovery effort is needed after a crash. Explain why this may
be the case.

Before transaction commitment, recovery involves reverting to the shadow page table, representing the pre-transaction state.

After commitment, the database is already in a consistent state due to the atomicity of the commit operation.

### Question 9: MTTF
[4 Marks]

Given some data to be put on disks, which one of the following RAID configurations will
have the best MTTF? Calculate each case and show your calculations with simple
explanations. Assume individual MTTF of the disks in this question are the same. 
```
(1) RAID0 with 3 disks, 
p(fail) = 3p
MTTF0 = 1/3p = 1/3 MTTF

(2) RAID 1 with 4 disks (for this case first disk is mirrored 3 times), 
p(fail) = p^4
MTTF0 = 1/p^4 = 1 / (MTTF)^4

(3) RAID 3 with 3 disks, 
p(fail) = C32 p^2
MTTF0 = 1/3p^2 = 1/3(MTTF)^2

(4) RAID 4 with 3 disks.
p(fail) = C32 p^2
MTTF0 = 1/3p^2 = 1/3(MTTF)^2
```
```{tip}
Usually assume that MTTF > 1. Hence (2) has the largest MTTF and is better. A larger MTTF is better because it indicates that the system or component has a longer expected time before it will fail. Hence larger MTTF is better.

```
### Question 10: Optimistic Concurrency Control & Snapshot Isolation
[4 Marks]

What is the difference between a classical Optimistic Concurrency control mechanism
versus a Snapshot Isolation-based one. What is the implication of this difference? Briefly
explain.

```{note}

Optimistic Concurrency Control (OCC) and Snapshot Isolation (SI) are both strategies used to manage concurrent transactions in a database system. However, they work quite differently:

1. **Optimistic Concurrency Control (OCC)**: OCC operates under the assumption that conflicts between transactions are rare. It allows multiple transactions to proceed without locking resources. OCC divides each transaction into three phases: read, validation, and write. During the read phase, changes are made to a private copy of the database. In the validation phase, the system checks to see if any other transaction has modified the data that was read. If there are no conflicts, the transaction proceeds to the write phase, where it applies its changes to the actual database. If a conflict is detected during the validation phase, the transaction is aborted and restarted.

2. **Snapshot Isolation (SI)**: SI, on the other hand, provides each transaction with a "snapshot" of the database at the start of the transaction. This snapshot represents a consistent state of the database. Transactions execute concurrently and write to the database without acquiring locks. Unlike OCC, it does not have a separate validation phase. If two transactions try to modify the same data, the second one to commit will be aborted to avoid a write-write conflict.

The primary difference between OCC and SI lies in how they handle conflicts. While OCC uses a validation phase to detect conflicts and aborts the transaction if any are found, SI allows transactions to proceed until a write-write conflict is detected, at which point the transaction is aborted. 

The implication of this difference is that SI may provide better performance than OCC in workloads where read-write conflicts are common but write-write conflicts are rare. However, SI can lead to an anomaly known as write skew, which does not occur under OCC. Therefore, the choice between OCC and SI depends on the specific workload and consistency requirements.
```

### Question 11: Join Calculation
[4 Marks]

Relation A has 1,000 records stored in 40 blocks that can be read consecutively.
Relation B has 800 records stored in 50 blocks that can be read consecutively. For a SQL
query with a join operation that joins these two relations, the query optimizer chooses to
use block nested-loop join. Should the outer relation be A or B based on the costs that
you may derive using the information above? Can we decide on this choice using the
information provided? If so, show your calculations and then give your answer, if not
briefly explain why not.

R: outer relation, S: inner relation

- Simple nested-loop join

    Block transfer = nr * bs + br
    
    Seeks = nr + br 

- Block nested-loop join

    Block transfer = br * bs + br

    Seeks = 2br

```
A: outer, B: inner
Block nested-loop join
Block transfer = nr * bs + br = 2040	
Seeks = 2br = 80

B: outer, A: inner
Block nested-loop join
Block transfer = nr * bs + br = 2050
Seeks = 2br = 100
```