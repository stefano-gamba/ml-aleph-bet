# AI Agent Guidelines & Security Best Practices

This document defines the operational rules, coding standards, and security best practices that every AI agent (including Google Antigravity, Gemini CLI, and other agentic assistants) must strictly follow when operating in this repository.

---

## 1. Language & Documentation Conventions

- **Repository Content in English**:
  - All project documentation (Markdown files, guides, design docs), source code identifiers, docstrings, and in-code comments must be written in **English**.
  - Commit messages and pull request descriptions must be written in **English**.
- **User Communication**:
  - Direct interaction in the chat/terminal interface should adapt to the language preferred by the user (e.g., Italian if addressed in Italian).

---

## 2. Command Execution & Sandboxing

- **Respect Sandbox Isolation**:
  - Always run terminal commands within the default sandbox with minimum necessary privileges.
  - Never bypass the sandbox (`BypassSandbox: true`) unless explicitly required (e.g., authorized package downloads or network port binding) and clearly explained to the user beforehand.
  - Never attempt to evade, disable, or alter execution confinement boundaries.
- **Prohibition of Destructive Commands**:
  - Do not run irreversible or destructive commands (e.g., recursive `rm -rf`, disk formatting, unvetted `git reset --hard`, `git push --force`, `git clean -fdx`) without explicit user consent.
  - Never execute remote scripts piped directly into shells (e.g., `curl ... | bash` or `wget ... | sh`).
  - Always inspect script contents before execution.

---

## 3. Secrets Management & Sensitive Data

- **Zero Hardcoded Secrets**:
  - Never commit, display, or hardcode credentials, passwords, private keys, API keys (Google Cloud, OpenAI, Anthropic, AWS, GitHub, etc.), or authentication tokens in source files, notebooks, or messages.
  - Always retrieve secrets from environment variables or ignored configuration files (e.g., `.env`).
- **Version Control Auditing**:
  - Before staging or committing files, ensure sensitive files are ignored via `.gitignore` (e.g., `.env`, `*.pem`, `*.key`, local credentials).
  - If plaintext secrets are detected in the repository or history, report them immediately to the user for rotation and redaction.
- **Privacy & PII Protection**:
  - Never exfiltrate personal data, proprietary datasets, internal logs, or confidential information to external third-party endpoints.

---

## 4. Python & Machine Learning Code Security

- **Safe Deserialization**:
  - **Avoid `pickle` on untrusted data**: Never call `pickle.load()` or `pickle.loads()` on model weights, checkpoints, or datasets from untrusted or external sources due to the risk of Remote Code Execution (RCE).
  - Prefer safe serialization formats such as `safetensors`, `json`, or `numpy.load` with `allow_pickle=False`.
  - For YAML configurations, always use `yaml.safe_load()` instead of `yaml.load()`.
- **Injection Prevention**:
  - Avoid dynamic code execution functions like `eval()`, `exec()`, or unsanitized shell wrappers (`os.system`).
- **Input Validation & Resource Limits**:
  - Validate shapes, data types, and value bounds of tensors and arrays prior to computation to prevent Out-Of-Memory (OOM) crashes, infinite loops, or Denial of Service (DoS).

---

## 5. Supply Chain & Dependency Hygiene

- **Controlled Installations**:
  - Do not install third-party packages or system dependencies without user confirmation or clear necessity.
  - Protect against typosquatting by double-checking package names on package registries (e.g., PyPI).
  - Pin package versions or specify compatibility ranges in `requirements.txt` / `pyproject.toml` and verify against known Common Vulnerabilities and Exposures (CVEs).

---

## 6. Access Control & Code Integrity

- **Principle of Least Privilege**:
  - Limit file modifications strictly to the files and directories relevant to the assigned task.
  - Do not alter system configurations, user files outside the workspace, or test/security harnesses.
- **No Protection Bypasses**:
  - Never attempt to bypass CAPTCHAs, bot protection gates, biometrics, firewalls, or proxy policies. If an action is blocked, report the block to the user.
- **Documentation & Review**:
  - Provide concise, transparent explanations for all proposed changes.
  - Preserve comments, existing code conventions, and license notices unless explicitly requested otherwise.
