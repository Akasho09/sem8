# PBFT (Practical Byzantine Fault Tolerance) — Detailed Notes
1. Byzantine Fault
- A Byzantine Fault occurs when a node in a distributed system behaves unpredictably or maliciously.
- A faulty node may:
    - send wrong messages,
    - behave maliciously,
    - act inconsistently,
    - send different information to different replicas,
    - refuse to respond.
- Example
- Suppose 4 replicas exist:
R1​,R2​,R3​,R4​
- If R1 sends: “YES” to R2 , “NO” to R3
    - then it is behaving Byzantine.

- Why Byzantine Faults are Dangerous
- They can cause:
    inconsistent state,
    double spending,
    conflicting decisions,
    system failure.
- PBFT is designed to tolerate such failures.

2. Deterministic Finality
- Once a block or transaction is committed:
    - it cannot be reverted,
    - no chain forks occur,
    - all honest nodes permanently agree.
- In PBFT
    - After consensus:
        - transaction becomes final immediately,
        - no need for multiple confirmations.
- Comparison with PoW
| Feature         | PBFT          | PoW               |
| --------------- | ------------- | ----------------- |
| Finality        | Deterministic | Probabilistic     |
| Forks           | No            | Possible          |
| Reversal Chance | None          | Small possibility |

## 3. Enterprise Blockchains
- PBFT is widely used in:
    enterprise blockchains,
    consortium networks,
    banking systems,
    permissioned ledgers.
- Why Enterprises Prefer PBFT
- Fast Transactions
    - Consensus occurs quickly.
- Energy Efficient
    - No mining required.
- Trusted Participants
    - Known validators reduce risk.
- Strong Consistency
    - All replicas maintain identical state.
- Examples
    - Hyperledger Fabric
    - Tendermint

## 4. PBFT Phases
- PBFT consensus occurs in multiple stages.
1. Phase 1: Pre-Prepare
Primary (leader) receives request from client.
- Primary assigns:
    sequence number,
    view number.
- Then broadcasts:
> PRE-PREPARE(v,n,d)
- Where:
    v = view number
    n = sequence number
    d = message digest
- Purpose
Ensures all replicas receive the same ordered request.

2. Phase 2: Prepare
- Replicas verify:
    digest,
    sequence number,
    message authenticity.
- Then broadcast:
> PREPARE(v,n,d,i)
- Requirement
    - Replica enters prepared state after receiving:
        2f+1
    matching PREPARE messages.
- Purpose
Ensures majority agreement on request order.

3. Phase 3: Commit
Replicas multicast:
> COMMIT(v,n,i)
- Requirement
    - Replica commits after receiving:
    2f+1
    matching COMMIT messages.
- Purpose
Guarantees all honest replicas execute same request.

## 5. Safety Property
- No two honest replicas decide differently.
- Meaning
    If one honest node commits transaction T,
    another honest node cannot commit conflicting transaction T′.
- Why Safety Holds
    - Because quorum intersection guarantees at least one honest replica overlap.

6. Liveness Property
- System eventually progresses.
- Meaning
    - Requests are eventually processed even if some nodes fail.
- Achieved Using
    timeouts,
    retransmissions,
    view change mechanism.

7. Weak Synchrony
- PBFT assumes:
    Weak Synchrony
    Messages are delivered within bounded delay eventually.
- Meaning
    Network may be temporarily slow,
    but not permanently asynchronous.
- Importance
- Without bounded communication delay:
    - replicas cannot distinguish:
        slow nodes
        faulty nodes.

## 8. View Change
- Purpose
Used when primary/leader becomes faulty.
- Trigger
    - Replicas detect:
        timeout,
        invalid messages,
        no progress.
- Process
1. Step 1
Replicas send:
VIEW-CHANGE 
message

2. Step 2
New primary selected.

3. Step 3
Consensus resumes.
New Leader Formula
- Usually:
Primary=vmodN
- Where:
v = current view number
N = total replicas

# 5. Hyperledger Fabric
- Enterprise-grade permissioned blockchain framework.
- Main characteristics:
    modular architecture
    pluggable consensus
    private channels
    no cryptocurrency required

## 16. MSP (Membership Service Provider)
- Handles:
    identity management
    participant authentication
    role validation
- Functions
- MSP:
    trusts specific Certificate Authorities
    maps certificates to roles
- Examples:
    Admin
    Peer
    Client
    Orderer

## 17. Certificate Authority (CA)
- Issues digital certificates.
- Certificates prove:
    identity
    authenticity

## 18. Digital Certificates
- Based on:
    - public key cryptography
- Contain:
public key
owner identity
CA signature

## 19. Channels in Hyperledger Fabric
- Private sub-networks inside Fabric.
- Purpose:
    maintain separate ledgers
    ensure confidentiality
- Benefits
    privacy
    isolated transactions
    restricted visibility

## 20. Endorsement vs Ordering
- Fabric separates:
1. (A) Endorsement
- Peers:
    simulate transaction
    verify smart contract logic

2. (B) Ordering
- Orderer nodes:
    decide transaction order
    package blocks

## 21. Modular Architecture
- Components are replaceable.
- Examples:
    consensus mechanisms
    databases
    identity systems

## 22. Blockchain in Supply Chain
- Advantages
1. (A) Tamper-Evident Audit Trail
Once data stored:
difficult to modify secretly.

2. (B) Transparency
- Participants can track:
    goods
    shipment history
    ownership

3. (C) Traceability
Track product origin.
- Useful in:
    food supply
    pharmaceuticals
    logistics

## 23. Immutability
- Blockchain data cannot be changed easily after confirmation.
- Achieved using:
    cryptographic hashing
    linked blocks

## 24. Consensus Mechanism
- Protocol that helps distributed nodes agree on a single state.
- Examples:
    PBFT
    PoW
    PoS
    Raft

## 25. Committee-Based Consensus
- Used in:
    Algorand
- Main Idea
    Small committee validates blocks instead of whole network.
- Benefits:
    scalability
    speed
    efficiency

## 26. VRF (Verifiable Random Function)
- Cryptographic function producing:
    random-looking output
    publicly verifiable proof
- Used for:
    random committee selection

## 27. Cryptographic Sortition
- Randomly selecting validators using VRFs.
- Benefits:
    unpredictable membership
    stronger security

## 28. Why Committee Rotation Matters
- Committee changes every round:
    - attackers cannot target validators easily
    - improves decentralization

## 29. Public vs Private Blockchain
| Feature    | Public    | Private            |
| ---------- | --------- | ------------------ |
| Access     | Open      | Restricted         |
| Validators | Anyone    | Approved members   |
| Example    | Ethereum  | Hyperledger Fabric |
| Identity   | Anonymous | Known              |

# 9. Important Formulas
1. Total Replicas Required
- PBFT tolerates: f
- Byzantine faulty replicas if:
> N=3f+1
- Where:
    N = total replicas
    f = faulty replicas
- Why 3f+1?
    - Need:
        f faulty replicas,
        2f+1 honest majority.
    - Thus:
        f+(2f+1)=3f+1

2. Quorum Size
Consensus quorum:
> Q=2f+1
- ie At least:
    2f+1
    matching messages required.

3. Honest Nodes in Quorum
From quorum:
> (2f+1)−f=f+1

4. Interpretation
- Even if:
    f replicas are malicious,
- there are still:
    - f+1 honest replicas remaining.

5. Quorum Intersection Property
- Two quorums always overlap in:
    - f+1 honest replicas.
- This Guarantees
    safety,
    consistency,
    no conflicting commits.

# 11. PBFT Workflow Summary
| Phase          | Action                    |
| -------------- | ------------------------- |
| Client Request | Client sends operation    |
| Pre-Prepare    | Leader proposes request   |
| Prepare        | Replicas verify and agree |
| Commit         | Replicas finalize         |
| Reply          | Response sent to client   |
