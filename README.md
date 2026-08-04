<h1 align="center">Hi 👋, I'm Adithya Azhagiri</h1>
<h3 align="center">Backend & Systems Engineer — PostgreSQL Internals · Full-Stack Development · Security-Minded</h3>

---

## 🚀 About Me

🔬 **Research Associate @ IIT-M Pravartak** — forked and extended PostgreSQL's C storage engine to add cryptographically tamper-evident tables

🎓 **B.Tech in Computer Science & Engineering (Cybersecurity)**, Shiv Nadar University Chennai | CGPA: **8.9**

🛡️ **Certified Ethical Hacker (CEH)** · Active OWASP Chennai Chapter Participant

🏆 **Head of Cognition** — SNUC Quiz Club

🎯 CTF & hackathon competitor — placements and finals across EditaCTF, PASSWORD CTF, Smart India Hackathon, and others (full list below)

📫 Reach me at **itsmeadithya.a@gmail.com**

---

## 🔬 Research & Experience — Featured

### 🏛️ Research Associate, IIT-M Pravartak
**Blockchain Integration in PostgreSQL Core**
`C` `PostgreSQL Internals (Table Access Methods, Shared Memory, LWLocks, SPI, Parser/Grammar, WAL)` `Concurrent Systems Design` `Cryptographic Hashing (SHA-256)`

This is the project I'd point to first: it's not an app built on top of a database, it's a modification to the database's own storage engine — the closest thing on my GitHub to what large-scale legacy/core-system work actually looks like.

- Built a custom PostgreSQL **Table Access Method** (~7,400 lines of C, modified PostgreSQL fork) enforcing cryptographic immutability at the storage-engine level — SHA-256 hash-chained rows, unconditional UPDATE/DELETE rejection — including a parser-grammar extension adding a first-class `CREATE BLOCKCHAIN TABLE` statement.
- **Root-caused a concurrency bug** causing 98.5% hash-chain corruption under concurrent inserts (1,290/1,310 broken links); redesigned the ordering system around **atomic per-table counters** and a **shared-memory cross-transaction hash cache**, achieving 100% integrity across all subsequent stress tests (32 concurrent clients, 100K-row transactions).
- Designed a **crash-safe, WAL-inspired recovery log** preserving hash-chain continuity across rollbacks and crashes with automatic replay on startup; measured **881 TPS at 10 concurrent clients** with only 6% insert-latency overhead vs. unmodified heap storage.

Co-filed a patent on the query-anchoring extension of this work through IITM Pravartak Technologies Foundation.

**Code:** [`postgres_test` (`blockchain-table` branch)](https://github.com/UltraMoonEagle/postgres_test/tree/blockchain-table) — full PostgreSQL fork with the storage-engine changes patched into `src/backend/access/`, `parser/`, and `commands/`.

---

## 🛠️ Tech Stack

### Languages
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)

### Backend & Frameworks
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)

### Databases & Storage
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)

### DevOps & Systems
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

### Security Tooling
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![Burp Suite](https://img.shields.io/badge/Burp_Suite-FF6633?style=for-the-badge&logo=burp-suite&logoColor=white)
![IDA Pro](https://img.shields.io/badge/IDA_Pro-00A4EF?style=for-the-badge&logo=ida&logoColor=white)

### Blockchain / Web3 (project work)
![Solidity](https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white)
![Move](https://img.shields.io/badge/Move-000000?style=for-the-badge&logo=aptos&logoColor=white)
![Ethereum](https://img.shields.io/badge/Ethereum-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white)
![IPFS](https://img.shields.io/badge/IPFS-65C2CB?style=for-the-badge&logo=ipfs&logoColor=white)

---

## 💼 Featured Projects

### 🔗 [FlowForge](https://github.com/UltraMoonEagle/FlowForge)
**Self-Built Workflow Automation Platform (n8n/Zapier-style)**
`NestJS` `TypeScript` `PostgreSQL` `Redis` `BullMQ` `React`

- DAG-based execution engine: builds a dependency graph from the workflow definition and executes it in topological order, with cycle detection
- Async job processing via a Redis-backed Bull queue, with per-node **exponential backoff + jitter** retry and timeout handling
- Structured execution logs and a dedicated error-tracking service, plus live status updates over WebSockets
- AES-256-GCM credential encryption (scrypt-derived keys) and a 40-permission RBAC system across 3 roles

### 🔐 [PenGUIn](https://github.com/fromjyce/PenGUIn) *(team project — contributor)*
**One-Click Ubuntu Hardening Application**
`PyGTK` `SQLite` `IPtables` `Linux Shell`

- GUI-based security hardening tool targeting **98% CIS Benchmark compliance**
- Integrated AIDE (intrusion detection) and 2FA, with an auto-updater for ongoing patches

### 📦 [Archiva](https://github.com/Adithya-A/archiva)
**Decentralized Smart Contract Archival Solution**
`Aptos Move` `zk-SNARKs` `IPFS` `Arweave` `React` `Solidity`

- Blockchain storage optimization for Ethereum/Polygon with **40% gas cost reduction** via IPFS/Arweave
- Zero-knowledge proofs for privacy-preserving archival

### 🦠 [MEMZ Analysis](https://github.com/Adithya-A/memz-analysis)
**Malware Analysis & Reverse Engineering**
`C++` `Windows API` `IDA Pro` `Shellcode`

- In-depth reverse engineering of MEMZ 4.0, with a full forensics report and mitigation strategies

---

## 🏆 Achievements & Certifications

### 🎓 Certifications
- 🛡️ **Certified Ethical Hacker (CEH)**

### 🚩 CTF Competitions
- 🥇 **1st Place** — EditaCTF
- 🏅 **4th Place** (out of 40+ teams) — PASSWORD CTF by VIT-C
- 🎖️ **Finalist** — VishwaCTF, EncryptID, BITs CTF, PragyaanCTF
- ✅ 30+ rooms on TryHackMe, all 34 NATAS and all 34 Bandit challenges (OverTheWire)

### 💻 Hackathons
- 🏆 **2x Finalist** — Smart India Hackathon (SIH)
- 🏆 **Finalist** — IIT Roorkee Road Safety Hackathon (70+ teams)
- 🚀 Participated in Walmart Sparkathon, Technica, and more

### 🎮 Community Impact
- 🤖 Designed & deployed a **Discord bot** reaching **1,200+ active players**

---

## 📫 Connect With Me

<p align="center">
  <a href="mailto:itsmeadithya.a@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
  </a>
  <a href="https://linkedin.com/in/adithya-azhagiri">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="https://tryhackme.com/p/AdithyaA">
    <img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="TryHackMe"/>
  </a>
</p>

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=100&section=footer" alt="footer"/>
</p>

<p align="center">
  <i>Adithya Azhagiri — let's build something amazing together!</i>
</p>
