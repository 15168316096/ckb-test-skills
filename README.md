# CKB Test Skills

This project contains auxiliary Skills for CKB (Common Knowledge Base) contract testing. It aims to help developers perform contract analysis and test case design more efficiently.

## Installation

To use the Skills in this project, you need to install the `openskills` tool first:

```bash
npm i -g openskills
openskills install gpBlockchain/ckb-test-skills
openskills sync
```

## Available Skills

### ckb-vm-contract-test-analysis

This Skill focuses on analyzing CKB smart contract code to assist in designing comprehensive test plans.

**Key Features:**
*   **Contract Logic Analysis**: Deeply understand the contract verification flow (e.g., Lock Script and Type Script).
*   **Test Scenario Generation**: Automatically suggest test scenarios (normal flows and edge cases) based on code logic.
*   **Data Structure Extraction**: Identify Args, Witness, and Cell Data structures used by the contract.

#### Usage

You can directly invoke this Skill to analyze specific contract files.
> **Note:** Please explicitly specify whether the target contract is a **Lock Script** or a **Type Script**, as the analysis logic and test scenarios differ significantly between them.

**Command Example:**

```text
Use ckb-vm-contract-test-analysis to perform test analysis on type contract <contract_file_path>
```

#### Practical Example: xUDT Contract Analysis

Taking `examples/xudt.c` in the project as an example:

```text
使用ckb-vm-contract-test-analysis 对type合约做测试分析 examples/xudt.c
```
*   [xudt OpenSkills Share Link](https://opncd.ai/share/zcgcPYsR)

#### Practical Example: commitment-lock Contract Analysis

Taking `examples/commitment-lock.rs` in the project as an example:

```text
使用ckb-vm-contract-test-analysis 对lock合约做测试分析 examples/commitment-lock.rs
```
*   [commitment-lock OpenSkills Share Link](https://opncd.ai/share/DxsUidbn)

### security-audit

This Skill provides an AI-driven security audit framework applicable to any programming language and project type.

**Key Features:**
*   **Phased Execution**: Structured workflow across 4 phases — reconnaissance, deep audit, documentation updates, and final report generation.
*   **Multi-Dimension Analysis**: Covers 13 audit dimensions including input validation, cryptography, authentication, business logic, memory safety, smart contract specifics, and more.
*   **TODO-Driven Tracking**: Uses a centralized TODO document as the single source of truth for audit progress, supporting cross-session continuity.
*   **CKB Memory Alignment Audit (DIM-CKB-ALIGN)**: Detects memory alignment issues specific to CKB-VM (RISC-V) smart contracts, including unaligned pointer casts, packed struct access, buffer alignment, Molecule data access, and VM version compatibility. Outputs a structured audit report with risk classification and fix suggestions.
*   **CKB RFC Compliance Matching (DIM-CKB-RFC)**: Cross-references CKB project code against [CKB RFCs](https://github.com/nervosnetwork/rfcs/tree/master/rfcs) to verify protocol compliance. Maps code modules to relevant RFCs (transaction structure, VM syscalls, serialization, token standards, etc.) and produces an RFC coverage matrix with deviation analysis.

#### Usage

```text
Use security-audit to perform a security audit on <project_path>
```

For CKB-specific memory alignment audit:

```text
Use security-audit to audit CKB contract memory alignment issues on <contract_file_path>
```

For CKB RFC compliance matching:

```text
Use security-audit to check CKB RFC compliance on <project_path>
```
