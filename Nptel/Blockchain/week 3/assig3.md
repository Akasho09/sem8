###
- OP_DROP → remove top
- OP_NIP → remove second-from-top
- OP_2DROP → remove top 2

## 🔍 What if transactions are odd?
- A Merkle tree is built by pairing transaction hashes and hashing them together until a single Merkle root is obtained.
- If the number of transactions is odd, the last hash has no pair.
- 👉 Solution:
    - The last hash is duplicated
    - Then paired with itself and hashed

##  Merkle Tree and Hash pointers 
> Merkle Tree → secures transactions within a block
> Hash pointers (prev hash) → secure blocks across the chain

## a) Safety ensures transactions are irreversible, while Liveness ensures transactions are eventually added.

 