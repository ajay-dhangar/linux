# Contributing to the Linux Engineering Roadmap

First off, thank you for taking the time to contribute! It is people like you who make the open-source community such a powerful place to learn, inspire, and create.

By contributing to this project, you agree to abide by its [Code of Conduct](./CODE_OF_CONDUCT.md).

---

## 🏗 What We Are Looking For
We welcome contributions that improve the quality and depth of this roadmap:
* **New Modules:** Deep dives into kernel internals, security hardening, or eBPF.
* **Refinement:** Correcting technical inaccuracies or updating commands for modern distros (e.g., transitioning from `iptables` to `nftables`).
* **Labs:** Practical hands-on exercises for existing phases.
* **Visuals:** Diagrams (Mermaid.js or high-quality SVG) that explain complex concepts like LVM or the TCP/IP stack.

---

## 🛠 Our Development Process

### 1. Reporting Bugs or Feature Requests
Before creating a new issue, please **search existing issues** to see if it has already been reported. 
* Use the **Bug Report** template for technical errors.
* Use the **Feature Request** template for new roadmap phases.

### 2. Fork & Branch
1.  **Fork** the repository to your own GitHub account.
2.  Create a branch from `main`. Use a naming convention like:
    * `feat/add-ebpf-module`
    * `fix/chmod-syntax-error`
    * `docs/update-lvm-diagram`

### 3. Standards & Style
To maintain a "World-Class" standard, please follow these guidelines:
* **Technical Accuracy:** Verify all commands in a fresh VM (Ubuntu 24.04+ or RHEL 9+) before submitting.
* **Tone:** Maintain an encouraging, engineering-focused, and concise tone.
* **Formatting:** Use standard Markdown. For complex math, use LaTeX syntax (e.g., $$ 2^n $$).
* **Commits:** Follow [Conventional Commits](https://www.conventionalcommits.org/):
    * `feat: add advanced shell debugging section`
    * `fix: corrected inode definition in storage phase`

---

## 🚀 Pull Request Guidelines
When you are ready to submit your changes:

1.  **Update Documentation:** Ensure your changes are reflected in the main `README.md` table of contents if necessary.
2.  **Detailed Description:** Explain *why* this change is necessary and *what* specific technical value it adds.
3.  **Self-Review:** Check for typos and broken links.
4.  **Stay Focused:** Keep PRs small. A PR that changes 50 files is harder to review than 5 PRs that change 10 files.

---

## ⚖️ License
By contributing, you agree that your contributions will be licensed under its **MIT License**.

---

## 💬 Questions?
If you have questions about a specific phase or want to discuss a major architecture change to the roadmap, please open a **Discussion** in the GitHub repository or contact the maintainer at [ajay.dhangar@example.com].

**Thank you for helping build the world's best Linux learning resource!** 🐧
