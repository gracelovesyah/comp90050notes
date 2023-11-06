

# Formula Sheet

## Communication Cost
- **Transmit Time**: $ \text{time} = \frac{\text{distance}}{c} + \frac{\text{message size (bits)}}{\text{bandwidth}} $
- **Speed of Light**: $ c = 200 \times 10^6 $ meters/second (in fiber optics)

## Joins and Query Cost
- **Simple Join Cost**: $ \text{cost} = n_r \times b_s + b_r \times (b_t) $
- **Nested Loop Join Cost**: $ \text{cost} = b_r \times b_s + b_r \times (b_t) $
- **Block Nested Loop Join Cost**: $ \text{cost} = 2 \times b_r \times (s) $

## Concurrency Control
- **Dekker's Algorithm**: Used to ensure mutual exclusion in concurrent programming.
- **Spin Locks**: A lock that causes a thread trying to acquire it to simply wait in a loop ("spin") while repeatedly checking if the lock is available.

## Two-Phase Locking (2PL)
- **Growing Phase**: Transaction may acquire locks.
- **Shrinking Phase**: Transaction may release locks but cannot acquire any new ones.

## Timestamp Ordering
- **Rule**: If a transaction $ T_i $ wants to read (or write) an object, and $ T_j $ has written (or read) that object with a later timestamp, $ T_i $ must wait or be rolled back.

## Two-Phase Commit (2PC)
- **Phase 1 (Voting Phase)**: Participants vote to commit or abort.
- **Phase 2 (Completion Phase)**: Based on voting, the transaction is either committed or aborted across all participants.

## RAID Levels
- **RAID 0**: Striping without redundancy.
- **RAID 1**: Mirroring.
- **RAID 5**: Striping with parity.
- **RAID 6**: Striping with double parity.

## Recovery
- **Log-based Recovery**: Uses a log to record the sequence of actions.
- **Checkpointing**: Technique to minimize the work needed to recover from a crash.

## ACID Properties
- **Atomicity**: Transactions are all-or-nothing.
- **Consistency**: Transactions transform the database from one valid state to another.
- **Isolation**: Transactions execute as if they are the only ones in the system.
- **Durability**: Once a transaction has been committed, it will remain so.

## Locks
- **Shared (S) Lock**: Allows concurrent transactions to read a database object.
- **Exclusive (X) Lock**: Allows a transaction to read and write a database object.

## Isolation Levels
- **Read Uncommitted**: Lowest level, transactions may read changes made by others before they commit.
- **Read Committed**: Transactions cannot read changes made by others until they commit.
- **Repeatable Read**: Ensures repeatable reads but may not prevent phantom reads.
- **Serializable**: Highest level, transactions are completely isolated from one another.

## Fault Tolerance
- **Mean Time To Failure (MTTF)**: Average time to failure for a system.
- **Mean Time To Repair (MTTR)**: Average time to repair a system.
- **Availability**: $ \text{Availability} = \frac{\text{MTTF}}{\text{MTTF} + \text{MTTR}} $

## CAP Theorem
- **Consistency**: Every read receives the most recent write or an error.
- **Availability**: Every request receives a (non-error) response, without guaranteeing that it contains the most recent write.
- **Partition Tolerance**: The system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes.

