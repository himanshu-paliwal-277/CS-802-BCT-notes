# Unit - 3

## Q.1 What is a Smart Contract in Blockchain?

A **smart contract** is a self-executing digital contract in which the **terms of agreement are written directly into code**. It automatically carries out actions (like transferring money or verifying a condition) when predefined conditions are met—**without needing a third party** like a lawyer, notary, or bank.

Smart contracts operate on blockchain platforms like **Ethereum**, and are key components of **decentralized applications (dApps)** and **DeFi (Decentralized Finance)**.

---

## 🧠 Key Characteristics of Smart Contracts

- **Autonomous**: Executes automatically without user intervention.
- **Immutable**: Once deployed to the blockchain, it cannot be changed.
- **Transparent**: Code is visible to all participants on the network.
- **Trustless**: Eliminates the need to trust a third party—trust is placed in the code.

---

## 🧾 Example: Freelance Payment Escrow Contract

### 🧪 Scenario:
A client hires a freelancer to create a website for **2 ETH**. The client wants to ensure the payment is made **only after** the work is completed. The freelancer wants assurance that the funds are reserved and will be released when the job is done.

### 👨‍💻 Simplified Smart Contract (Solidity Pseudocode):

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Escrow {
    address public client;
    address public freelancer;
    uint public amount = 2 ether;
    bool public workCompleted;

    constructor(address _freelancer) payable {
        require(msg.value == amount, "Must deposit exactly 2 ETH");
        client = msg.sender;
        freelancer = _freelancer;
    }

    function confirmWorkCompleted() public {
        require(msg.sender == client, "Only client can confirm");
        workCompleted = true;
    }

    function releasePayment() public {
        require(workCompleted, "Work not completed");
        payable(freelancer).transfer(amount);
    }
}
```

## ⚙️ How It Works

1. The **client** deploys the contract and sends `2 ETH` to it.
2. The **freelancer** completes the job.
3. The **client confirms** completion by calling `confirmWorkCompleted()`.
4. The **smart contract releases** the `2 ETH` to the freelancer when `releasePayment()` is called.

---

## 🔐 Benefits of Smart Contracts

| Feature             | Description                                                              |
|---------------------|--------------------------------------------------------------------------|
| 💡 **Automation**    | Automatically executes actions when conditions are met                   |
| 🔒 **Security**      | Stored on a secure blockchain and resistant to tampering                 |
| 🧾 **Transparency**  | Code is publicly accessible for audit and verification                   |
| ⏱️ **Efficiency**    | Reduces delays and costs by removing intermediaries                      |
| ❌ **No Intermediary**| Trust is placed in the code, not in a third party                        |

---

## 🪙 Blockchain Platforms that Support Smart Contracts

Here are popular blockchain platforms that support the development and execution of smart contracts:

- **Ethereum** – The pioneer of smart contracts and dApps.
- **BNB Smart Chain (BSC)** – A faster and cheaper alternative to Ethereum.
- **Polygon (MATIC)** – A Layer 2 scaling solution for Ethereum with lower gas fees.
- **Solana** – Known for high-speed and low-cost transactions.
- **Cardano** – Uses a research-driven approach with formal verification.
- **Avalanche** – Highly scalable and supports multiple virtual machines.
- **NEAR Protocol** – Developer-friendly and sharding-based scalability.
- **Tezos** – Focuses on formal verification and self-amending ledger.
- **Algorand** – A fast blockchain with strong academic foundations.
- **Fantom** – Optimized for DeFi and fast transaction throughput.

---

## 🧩 Real-World Use Cases of Smart Contracts

Smart contracts have many applications across industries:

- **DeFi (Decentralized Finance)**: Lending, borrowing, staking, and yield farming without banks.
- **NFTs (Non-Fungible Tokens)**: Ownership and royalties for digital art and collectibles.
- **DAOs (Decentralized Autonomous Organizations)**: Community-driven governance systems.
- **Supply Chain Management**: Tracking goods transparently and verifying authenticity.
- **Voting Systems**: Tamper-proof digital voting for elections or corporate governance.
- **Insurance**: Automated claim approvals and payouts based on conditions.
- **Gaming**: In-game assets and rewards managed through contracts.

---

## 🧠 Summary

Smart contracts are digital agreements that run on the blockchain and execute automatically when conditions are met. They eliminate the need for trust and middlemen, **reducing cost, time, and risk** in digital transactions.

They are the building blocks of **Web3** and a foundation for innovation in **finance, art, governance, logistics, and more**.

---

## Q.2 Write a smart contract in Solidity to store student data.

// SPDX-License-Identifier: MIT
```
pragma solidity ^0.8.0;

contract StudentRecords {
    
    struct Student {
        string name;
        uint age;
        string course;
    }

    // Mapping from student address to their data
    mapping(address => Student) private students;

    // Event to log when student data is stored
    event StudentAdded(address indexed studentAddress, string name, uint age, string course);

    // Function to add or update student data
    function addOrUpdateStudent(string memory _name, uint _age, string memory _course) public {
        students[msg.sender] = Student(_name, _age, _course);
        emit StudentAdded(msg.sender, _name, _age, _course);
    }

    // Function to retrieve student data
    function getStudent(address _studentAddress) public view returns (string memory, uint, string memory) {
        Student memory s = students[_studentAddress];
        return (s.name, s.age, s.course);
    }
}

```

## Q.3 What is a smart contract and how is it used in the Ethereum blockchain? 

## 📜 What is a Smart Contract?

A **smart contract** is a self-executing digital agreement written in code, where the terms of the agreement are embedded within the contract itself. It runs on a blockchain and automatically performs actions when predefined conditions are met—**without the need for intermediaries or third parties**.

Smart contracts are immutable (cannot be changed once deployed) and decentralized (executed by the blockchain network). They are the core building blocks of **Decentralized Applications (dApps)**.

---

## 🛠️ How Smart Contracts Work on Ethereum

## 1. **Written in Solidity**
Smart contracts on Ethereum are typically written in a language called **Solidity**, designed to work with the Ethereum Virtual Machine (EVM).

## 2. **Deployment to Blockchain**
Once developed, a smart contract is **deployed to the Ethereum blockchain**, which assigns it a unique address. From this point, it becomes public and immutable.

## 3. **Interaction**
Users interact with smart contracts by calling their functions. These interactions are recorded as **transactions** on the blockchain.

## 4. **Gas Fees**
Each interaction with a smart contract consumes **"gas"**, a fee paid in ETH that compensates Ethereum nodes for computation.

---

## ✅ Example Use Case: Escrow Payment

Let’s say a client wants to hire a freelancer:

1. The client deploys a smart contract and sends 2 ETH to it.
2. The freelancer does the work.
3. Once the client confirms the job is done, the smart contract releases the 2 ETH to the freelancer.

Everything happens automatically **without the need for a third-party escrow service**.

---

## 🔐 Benefits of Smart Contracts

| Feature             | Description                                                              |
|---------------------|--------------------------------------------------------------------------|
| 💡 **Automation**    | Automatically executes actions when conditions are met                   |
| 🔒 **Security**      | Stored on a secure blockchain and resistant to tampering                 |
| 🧾 **Transparency**  | Code is publicly accessible for audit and verification                   |
| ⏱️ **Efficiency**    | Reduces delays and costs by removing intermediaries                      |
| ❌ **No Intermediary**| Trust is placed in the code, not in a third party                        |

---

## 🪙 Ethereum's Role in Smart Contracts

Ethereum was the **first blockchain platform** to introduce and support smart contracts at scale. It provides:

- **Ethereum Virtual Machine (EVM)**: The environment in which contracts run.
- **Solidity**: A developer-friendly language for writing contracts.
- **Gas Mechanism**: To manage fees and computational resources.

---

## 🔚 Summary

A smart contract is a revolutionary concept that allows for **trustless and automated agreements**. Ethereum brought this idea to life and made it accessible through its developer tools and decentralized network. Today, smart contracts are powering everything from **DeFi** to **NFTs**, **DAOs**, **gaming**, and much more.

They are the **foundation of Web3**.

---