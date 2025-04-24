# Unit - 2

## Q.1 What is a Hash Function?

A **hash function** is a cryptographic algorithm that takes input data of any size and produces a fixed-size output (called a hash or digest). It is widely used in blockchain to ensure **data security**, **immutability**, and **efficient verification**.

---

## 📋 Properties of a Hash Function (in Table)

| 🔢 Property          | 📖 Description                                                                |
| -------------------- | ----------------------------------------------------------------------------- |
| Deterministic        | The same input will always produce the same output.                           |
| Fast Computation     | Should be computationally efficient to calculate the hash value.              |
| Pre-image Resistance | It should be computationally infeasible to reverse the hash to get the input. |
| Avalanche Effect     | A small change in input drastically changes the output hash.                  |
| Collision Resistance | It should be hard to find two different inputs that produce the same hash.    |
| Fixed Output Size    | The output hash should always be of a fixed length, regardless of input size. |

---

## Q.2 What is Proof of Work (PoW)?

**Proof of Work (PoW)** is a consensus mechanism used in blockchain networks to validate transactions and add new blocks securely. It requires participants, known as **miners**, to solve complex mathematical puzzles to prove that a certain amount of computational work has been done.

---

## ⚙️ How Does Proof of Work Work?

1. **Transaction Collection**:
   - Users broadcast transactions to the network.
   - Miners collect these into a block.

2. **Miners Compete**:
   - Each miner tries to find a **nonce** that, when hashed with the block's data, produces a hash below a certain **target value**.

3. **Hash Function**:
   - PoW uses cryptographic hash functions like `SHA-256`.
   - A hash is a fixed-length string output derived from input data.

4. **The Puzzle**:
   - The goal is to find a nonce such that:
     ```
     hash(block data + nonce) < target
     ```

5. **Solution and Validation**:
   - The first miner to solve the puzzle shares the solution.
   - Others verify it.
   - If valid, the block is added to the blockchain.

6. **Rewards**:
   - The winning miner earns:
     - **Block reward** (e.g., Bitcoin)
     - **Transaction fees**

7. **Repeat**:
   - The process repeats for the next block.

---

## 🔒 Why is PoW Secure?

- Requires **significant computational work**, deterring attacks.
- To alter a block, an attacker would need to redo PoW for it **and all following blocks**.
- This makes tampering **economically unfeasible**.

---

## 📉 Drawbacks of PoW

| Drawback                | Description |
|-------------------------|-------------|
| ⛽ **High Energy Usage** | Mining consumes large amounts of electricity. |
| 🏭 **Environmental Impact** | Often powered by fossil fuels. |
| 🐢 **Slower TPS**        | E.g., Bitcoin handles 3–7 transactions/second. |
| 🏢 **Mining Centralization** | Powerful mining farms dominate the network. |

---

## 🪙 Examples of PoW Blockchains

- **Bitcoin (BTC)**
- **Litecoin (LTC)**
- **Ethereum (ETH)** *(before 2022 switch to PoS)*

---

## 🆚 PoW vs PoS

| Feature               | Proof of Work (PoW)                     | Proof of Stake (PoS)                          |
|----------------------|------------------------------------------|-----------------------------------------------|
| Resource Used         | Computational Power (Energy)            | Stake (Coins Locked in Network)              |
| Security              | Based on Hashing and Work               | Based on Economic Incentives                 |
| Environment Impact    | High                                    | Low                                           |
| Speed                 | Slower                                  | Faster                                        |

---

## 🧩 Summary

Proof of Work is the **original blockchain consensus algorithm**, offering strong security through computational difficulty. However, it comes with **energy inefficiency** and **scalability limitations**, which has led many newer blockchains to adopt alternatives like **Proof of Stake**.

## Q.3 Discuss the working of a digital signature.

A **digital signature** is a cryptographic technique used to validate the authenticity and integrity of a message, software, or digital document. It serves the same purpose as a handwritten signature or a stamped seal, but it is much more secure.

---

## 🔐 Working of a Digital Signature

The digital signature process involves **two main operations**:

1. **Signing**
2. **Verification**

These operations use **asymmetric cryptography** involving a **public key** and a **private key**.

---

## ✅ Steps Involved in Creating a Digital Signature

### 1. Hashing the Message
- A **hash function** (like SHA-256) is applied to the original message or document.
- This produces a **fixed-size hash value** (also called a message digest).
- Hashing ensures that even a small change in the message results in a completely different hash.

### 2. Encrypting the Hash with Private Key
- The sender encrypts the hash using their **private key**.
- This encrypted hash is called the **digital signature**.
- The digital signature is then sent along with the original message.

---

## 🔍 Steps Involved in Verifying a Digital Signature

### 1. Hashing the Received Message
- The receiver hashes the original message using the same hash function as the sender.

### 2. Decrypting the Signature
- The receiver decrypts the digital signature using the **sender’s public key**.
- This gives the **original hash value** that the sender had calculated.

### 3. Comparing Both Hashes
- The receiver compares the **calculated hash** with the **decrypted hash**.
- If both match, the message is **authentic** and **untampered**.
- If they don't match, it means the message has been **altered** or is **not from the claimed sender**.

---

## 🛡️ Importance of Digital Signatures

- ✅ **Authentication**: Confirms the identity of the sender.
- 🔄 **Integrity**: Ensures the message has not been altered.
- 🚫 **Non-repudiation**: The sender cannot deny having sent the message.

---

## 📌 Conclusion

Digital signatures provide a secure and efficient way to verify the authenticity and integrity of digital information. They are widely used in blockchain technology, email security, software distribution, and legal digital documents.

## Q.4 Which cryptographic algorithm is used in Blockchain? Explain in detail.

Blockchain technology relies on cryptographic algorithms to ensure security, integrity, and trust among participants in a decentralized network.

---

## 🔐 Common Cryptographic Algorithms Used in Blockchain

### 1. **Hashing Algorithms**

#### ➤ SHA-256 (Secure Hash Algorithm - 256 bit)
- Used in **Bitcoin** and many other blockchains.
- Produces a **256-bit fixed-length output** (called a hash) from any input.
- The process is **one-way** — it’s easy to compute a hash but almost impossible to reverse it.
- Even a small change in input results in a completely different hash (known as the **avalanche effect**).

**Example:**

Input: "Blockchain" SHA-256 Hash: 625da44a0670d0731e08d54c98605f7313a2ad02e4bbdc5a64e1577e0f6c7969


#### ➤ Keccak-256
- Used by **Ethereum**.
- Functions similarly to SHA-256 but is based on the Keccak family (standardized as SHA-3).

---

### 2. **Asymmetric Encryption Algorithms**

#### ➤ ECDSA (Elliptic Curve Digital Signature Algorithm)
- Used for **digital signatures** in Bitcoin and Ethereum.
- It uses a **public-private key pair**:
  - **Private Key**: Used to sign the transaction.
  - **Public Key**: Used to verify the transaction.
- Ensures **authentication**, **data integrity**, and **non-repudiation**.

---

## 📌 Summary Table

| Purpose               | Algorithm Used        |
|----------------------|-----------------------|
| Hashing              | SHA-256, Keccak-256   |
| Digital Signatures   | ECDSA                 |
| Key Pair Generation  | ECC (Elliptic Curve Cryptography) |

---

## Q.5 What are some common validation techniques used in blockchain systems, such as Proof-of-Work and Proof-of-Stake?

To maintain a decentralized and trustless network, blockchain systems use **consensus mechanisms** to validate transactions and add new blocks.

---

## ⛏️ 1. Proof-of-Work (PoW)

### ➤ How It Works:
- Miners solve complex mathematical puzzles.
- The first to solve it gets to **add the next block** and receive a reward (e.g., Bitcoin).
- The puzzle difficulty adjusts to ensure regular block intervals.

### ➤ Features:
- **Used by**: Bitcoin, Litecoin.
- **Pros**: High security, well-tested.
- **Cons**: High energy consumption, slow transactions.

---

## 🌱 2. Proof-of-Stake (PoS)

### ➤ How It Works:
- Validators are selected based on the number of coins they **stake** (lock up).
- The more coins staked, the higher the chance of being chosen to validate the next block.

### ➤ Features:
- **Used by**: Ethereum 2.0, Cardano, Solana (uses hybrid PoS/PoH).
- **Pros**: Energy efficient, faster, scalable.
- **Cons**: Potential centralization if a few users hold large amounts of crypto.

---

## 🔁 Other Popular Consensus Mechanisms

| Mechanism              | Description |
|------------------------|-------------|
| **Delegated Proof-of-Stake (DPoS)** | Stakeholders vote for delegates to validate blocks. Used by EOS. |
| **Proof-of-Authority (PoA)**       | Trusted validators are pre-approved. Used in private networks. |
| **Proof-of-History (PoH)**         | Used by Solana. Adds timestamps to transactions to improve speed. |
| **Practical Byzantine Fault Tolerance (PBFT)** | Used in permissioned blockchains like Hyperledger. Prevents malicious consensus among known nodes. |

---

## 📌 Conclusion

Blockchain technology uses a combination of **cryptographic algorithms** and **consensus mechanisms** to provide security, decentralization, and immutability. The choice of hashing and consensus method depends on the blockchain's use case:

- **PoW**: Secure but energy-intensive.
- **PoS**: Energy-efficient and scalable.
- **Cryptography** (like SHA-256 and ECDSA): Ensures privacy, authentication, and trust.

These elements together form the backbone of blockchain security and functionality.

---

## Q.6 What is Double Spending? Is it possible to double spend in a Blockchain system?

---

## 💸 What is Double Spending?

**Double spending** is a type of **fraud** in digital currency systems where the same digital token or cryptocurrency is spent **more than once**.

Unlike physical cash (which can only be handed to one person at a time), digital currency can be **copied and reused** unless proper mechanisms are in place to prevent it.

### ➤ Example:
Imagine a user has 1 BTC. They try to send this same BTC to **two different merchants** at the same time. Without proper checks, both merchants might think they have received payment — but in reality, only one can actually receive it.

---

## 🔒 Is Double Spending Possible in Blockchain?

In traditional systems, central authorities like banks prevent double spending. But in **decentralized systems like blockchain**, there's **no central authority**, so special mechanisms are needed to avoid double spending.

### ✅ Blockchain Prevents Double Spending Using:

---

### 1. **Consensus Mechanisms**

#### ➤ Proof-of-Work (PoW)
- Transactions are validated by miners.
- Once a block is added to the blockchain, it's extremely hard to change.
- Any conflicting transaction (like a double spend) will be **rejected by the network**.

---

### 2. **Transaction Confirmation**
- Once a transaction is included in a block and several more blocks are added after it (called **confirmations**), the transaction is considered **final and irreversible**.
- The more confirmations, the lower the chance of a successful double spend.

---

### 3. **Distributed Ledger**
- Every node in the network has a copy of the blockchain.
- If someone tries to double spend, the invalid transaction will be **detected and rejected** by other nodes.

---

## ❗ When is Double Spending Still a Risk?

While rare, certain situations can still pose a risk:

### ➤ 1. **51% Attack**
- If an attacker gains control of more than 50% of the network’s mining power, they could potentially:
  - Create a private fork of the blockchain.
  - Reverse transactions.
  - Enable double spending.
- However, this is extremely expensive and impractical for large blockchains like Bitcoin.

### ➤ 2. **Zero-Confirmation Transactions**
- If a merchant accepts a transaction **before it’s confirmed**, there's a small risk the transaction could be replaced in a different block.
- This is why high-value transactions require **multiple confirmations**.

---

## ✅ Conclusion

- **Double spending** is a serious issue in digital currency systems, but blockchain effectively prevents it through:
  - **Consensus algorithms**,
  - **Public ledger transparency**, and
  - **Cryptographic security**.
- As long as users follow best practices (like waiting for confirmations), double spending is **virtually impossible** in a secure blockchain network.

---

## Q.7 Compare HashCash PoW (Proof of Work) with Bitcoin PoW. Also discuss various types of attacks on PoW.

---

## 🔁 Comparison: HashCash PoW vs Bitcoin PoW

| Feature                  | **HashCash PoW**                                | **Bitcoin PoW**                                  |
|--------------------------|--------------------------------------------------|--------------------------------------------------|
| **Purpose**              | Initially designed to combat **email spam**     | Used to **secure blockchain** and add new blocks |
| **Introduced By**        | Adam Back (1997)                                 | Satoshi Nakamoto (2008)                          |
| **Use Case**             | Email systems (proof to send email)              | Cryptocurrency mining (validate transactions)    |
| **Input Data**           | Email header + timestamp                         | Block header (includes nonce, previous hash, etc.) |
| **Puzzle Solving**       | Find a nonce such that hash has N leading zeros | Same, but with dynamically adjusted difficulty   |
| **Difficulty Adjustment**| Not adaptive                                     | Adjusts every 2016 blocks (~2 weeks in Bitcoin)  |
| **Reward System**        | No reward; only access granted (e.g., email)     | Block rewards + transaction fees for miners      |

---

## ⚠️ Attacks on PoW (Proof of Work)

Despite being a robust mechanism, PoW is still vulnerable to some attacks:

---

### 1. **51% Attack**

- Occurs when a single miner or group gains more than **50% of total network hashing power**.
- They can:
  - Reverse transactions.
  - Double spend coins.
  - Prevent other miners from confirming blocks.

✅ **Mitigation**: Requires enormous computational power in major networks like Bitcoin, making it costly and impractical.

---

### 2. **Selfish Mining Attack**

- Malicious miners **withhold blocks** they find instead of broadcasting them.
- Aim: Create a private fork and force others to waste effort on a stale chain.
- Can lead to unfair rewards and centralization.

✅ **Mitigation**: Improve reward mechanisms and make selfish mining unprofitable through protocol updates.

---

### 3. **Denial of Service (DoS) Attack**

- Attackers flood the network with **invalid or spam transactions** to overload nodes.
- Can delay transaction processing and slow down the network.

✅ **Mitigation**: Transaction fees act as a deterrent. Nodes discard invalid transactions.

---

### 4. **Block Withholding Attack**

- A miner in a mining pool finds a valid block but **doesn’t submit it**.
- Goal: Harm the pool’s revenue and reputation.

✅ **Mitigation**: Detecting abnormal miner behavior and rewarding based on shares.

---

### 5. **Timejacking Attack**

- Alters a node’s **system time** to mislead the blockchain about block timestamps.
- Can disrupt the synchronization of blocks.

✅ **Mitigation**: Bitcoin limits timestamp deviation from the network median.

---

## 🧾 Conclusion

- **HashCash PoW** and **Bitcoin PoW** both rely on solving cryptographic puzzles, but they serve different purposes.
- Bitcoin improved upon HashCash by introducing incentives, decentralization, and dynamic difficulty adjustment.
- Though PoW is secure, it must constantly evolve to defend against attacks like **51% attacks**, **selfish mining**, and **DoS** threats.

---

## Q.8 Explain Byzantine Algorithm.  

## 🧠 Byzantine Algorithm (Byzantine Fault Tolerance)

### 🔷 What is the Byzantine Generals Problem?

The **Byzantine Generals Problem** is a famous issue in distributed computing that illustrates the **difficulty of achieving consensus** in the presence of **malicious or faulty nodes**.

Imagine several generals trying to agree on a common strategy. Some of them may be **traitors** who send **conflicting or false messages**. The challenge is:  
> **How can honest parties reach agreement even if some members are unreliable or dishonest?**

---

### 🛠️ Byzantine Fault Tolerance (BFT)

**Byzantine Fault Tolerance (BFT)** is the property of a distributed system to **reach consensus** even if **some nodes fail or act maliciously**.

- A system is said to be BFT if it can tolerate up to **(n−1)/3** faulty nodes in a network of **n nodes**.
- This means, in a 10-node network, up to **3 nodes can be faulty**, and the system will still function correctly.

---

### ✅ Key Points:
- Ensures consensus even in **hostile environments**.
- Used in **permissioned blockchains** like **Hyperledger Fabric**.
- Classic algorithm: **Practical Byzantine Fault Tolerance (PBFT)**.

---

##  Q.9 Explain Proof of Elapsed Time (PoET)

## 🔐 Proof of Elapsed Time (PoET)

### 🌐 What is PoET?

**Proof of Elapsed Time** is a **consensus algorithm** developed by Intel, designed for **permissioned blockchain networks**. It uses a **trusted execution environment (TEE)** like **Intel SGX** to ensure fairness and efficiency.

---

### ⚙️ How PoET Works:

1. Each participant (node) requests a **random wait time** from their TEE.
2. All nodes "sleep" for their assigned time.
3. The node with the **shortest wait time** wakes up first and **proposes the next block**.
4. The TEE ensures that the wait time is:
   - Random
   - Fair
   - Not tampered with

---

### ✅ Advantages of PoET:

- **Energy-efficient** compared to Proof-of-Work (no heavy computation).
- **Fair** — every node has an equal chance of being selected.
- **Secure** — trust is rooted in Intel's secure hardware (SGX).

---

### ❗ Limitations:

- **Centralized dependency** on Intel SGX.
- Vulnerable if SGX is compromised.
- Best suited for **enterprise/private blockchains**.

---

## 📌 Summary Table

| Feature                        | Byzantine Algorithm (BFT)                      | Proof of Elapsed Time (PoET)                      |
|-------------------------------|-----------------------------------------------|--------------------------------------------------|
| Purpose                       | Achieve consensus despite malicious nodes     | Select block proposer fairly and efficiently     |
| Network Type                  | Permissioned/consortium                       | Permissioned                                     |
| Trust Model                   | Tolerates faulty nodes                        | Relies on Trusted Execution Environment (TEE)    |
| Energy Efficiency             | High                                           | Very high (energy-efficient)                     |
| Common Use                    | Hyperledger Fabric, Tendermint                | Hyperledger Sawtooth                             |

