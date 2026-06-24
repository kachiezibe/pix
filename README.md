# Pix — Modular Multi-Agent AI Orchestration Layer & Claude Code State Machine

`pix` is an advanced, custom-configured **Model Context Protocol (MCP)** state machine and orchestrator designed to integrate seamlessly with **Claude Code** and other agentic developer workflows. It establishes a federated, self-learning network of specialized AI workers to coordinate research, code modification, automated testing, and security auditing.

## 🚀 Key Architectural Features

1. **Federated Hierarchical-Mesh Swarms:**
   - Moves away from simple single-agent prompting in favor of addressable, named workers (`coder`, `reviewer`, `tester`, `system-architect`, `security-auditor`).
   - Implements **SendMessage-First coordination** where agents communicate asynchronously, executing pipeline (sequential), fan-out (parallel), or supervisor patterns rather than polling shared states.
2. **Hybrid Vector Memory Graph:**
   - Combines a localized, high-performance **HNSW (Hierarchical Navigable Small World)** vector index (`ruvector.db`) with relational persistence.
   - Automatically indexes codebase structural patterns, custom APIs, and resolved debug cycles to achieve continuous self-learning across sessions.
3. **Custom Model Routing & Dispatch:**
   - Implements a **3-tier execution structure** (WASM-based local booster engines, speed-optimized models like Claude Haiku, and reasoning-heavy models like Claude Sonnet/Opus) to maximize resource efficiency.
   - Leverages **pre-task semantic mapping** and **post-task auditing** to ensure absolute execution precision.
4. **Lifecycle Hooks & Background Workers:**
   - Features automated system boundaries that trigger security audits (`aidefence_scan`), PII identification (`aidefence_has_pii`), and performance benchmarks post-success.

---

## 📂 Configuration Mapping

* **`.mcp.json`:** Direct server-start settings defining CLI executors, node topologies, and memory backend parameters.
* **`CLAUDE.md`:** Core engineering rules, SendMessage team spawning protocols, swarm topologies, and CLI references.
* **`.gitignore`:** Formulated to strictly isolate the local SQLite database layers (`ruvector.db`, `.swarm/memory.db*`), OS metadata (`.DS_Store`), and Claude Flow log directories to ensure absolute privacy.

---

## 🛠️ Commands Quick Reference

```bash
# Initialize and setup the multi-agent swarm
npx @claude-flow/cli@latest swarm init --topology hierarchical-mesh --max-agents 15

# Search codebase memory patterns
npx @claude-flow/cli@latest memory search --query "[keywords]" --namespace patterns

# Run diagnostics and automated fixes
npx @claude-flow/cli@latest doctor --fix

# Trigger post-change security sweeps
npx @claude-flow/cli@latest hooks worker dispatch --trigger audit
```
