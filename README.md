# ⚙️ grantboard-contracts

> Soroban smart contracts for GrantBoard — a decentralized grant management platform built on Stellar.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-active-brightgreen)
![Built With](https://img.shields.io/badge/built%20with-Rust%20%7C%20Soroban-informational)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Contract Functions](#-contract-functions)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Testing](#-testing)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌐 Overview

`grantboard-contracts` contains the on-chain logic powering GrantBoard's decentralized grant lifecycle. Written in Rust and deployed via [Soroban](https://soroban.stellar.org/), these contracts handle the full flow from grant creation through milestone-based fund release — trustlessly, on Stellar.

The contract enforces:

- **Locked funding** — grant funds are held in the contract until milestones are approved, not held by any individual party
- **Permissioned actions** — only the designated reviewer can select applicants and approve milestones
- **Milestone-based payouts** — funds are released incrementally as work is verified, reducing risk for all parties

---

## 📋 Contract Functions

| Function | Caller | Description |
|---|---|---|
| `create_grant` | Grant poster | Post a grant and lock funds into the contract |
| `apply` | Contributor | Submit an application for an open grant |
| `select_applicant` | Reviewer | Select a contributor from the applicant pool |
| `approve_milestone` | Reviewer | Approve a milestone and release the associated funds |
| `get_grant` | Anyone | Read current grant state and metadata |

---

## 📁 Project Structure

```
contracts/
└── grantboard/
    └── src/
        ├── lib.rs      # Core contract logic
        └── test.rs     # Unit tests
```

---

## 🚀 Getting Started

### Prerequisites

- [Rust](https://www.rust-lang.org/tools/install)
- [Stellar CLI](https://developers.stellar.org/docs/tools/stellar-cli)

### Install Rust & WASM Target

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add wasm32-unknown-unknown
```

### Install Stellar CLI

```bash
cargo install --locked stellar-cli
```

### Build the Contract

```bash
stellar contract build
```

The compiled `.wasm` file will be output to `target/wasm32-unknown-unknown/release/`.

---

## 🧪 Testing

Unit tests are co-located in `src/test.rs` and use the Soroban SDK test utilities.

```bash
cargo test
```

All tests must pass before opening a pull request.

---

## 🤝 Contributing

Contributions are welcome — whether it's a bug fix, gas optimization, or a new contract feature.

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature`
3. **Make** your changes and ensure all tests pass: `cargo test`
4. **Commit** using conventional commits: `git commit -m "feat: describe your change"`
5. **Open** a Pull Request against `main`

Please keep PRs focused and include test coverage for any new contract logic.

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.
