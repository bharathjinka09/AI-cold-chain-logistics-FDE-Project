# AI Forward Deployed Engineer Project

# Cold Chain Logistics — FDE Project

An experimental Python project providing a Streamlit-based UI, agent orchestration, and data-ingest tools for working with policies, SOPs, and legacy datasets used in cold-chain logistics workflows. It bundles agent tooling, an orchestrator, and ingestion scripts (including a Pinecone ingestion helper) so you can build a searchable knowledge layer and interactive UI for decision-support or documentation lookups.

## Quick summary
- Local UI: src/ui.py (Streamlit-based interface).
- Agent orchestration & helpers: src/orchestrator.py and src/agent_tools.py.
- Ingestion scripts for knowledge data: scripts/ingest_sop_pinecone.py and scripts/ingest_legacy_data.py.
- Documentation and usage notes: docs/instrutions.md and notes.pdf.

---

## What this is
A Python project combining a simple Streamlit UI, agent orchestration code, and data ingestion utilities to turn SOPs, legacy documents, and policy text into a queryable/agent-driven workflow useful for cold-chain logistics research and demonstrations.

### Stack
- Language(s): Python (primary)
- Framework / runtime: Streamlit (UI)
- Notable integrations (explicit in the repo):
  - Pinecone ingestion script present (scripts/ingest_sop_pinecone.py) — indicates vector database integration for semantic search.
  - A system prompt exists at src/prompts/system_prompt.txt — indicates LLM-agent usage for orchestration.
- Dependency list: requirements.txt (use this to install exact packages).

---

## How it's organized
```
.github/                     repo config (GitHub workflows, if any)
.streamlit/                  Streamlit config (config.toml)
Misc/                        miscellaneous materials and assets (Misc/Materials)
data/
  cache/                     runtime cache
  policy/                    policy documents and outputs
  raw/                       raw source documents
  source/                    original source files
docs/
  instrutions.md             usage instructions and notes
notes.pdf                    project notes (detailed PDF)
requirements.txt             Python dependencies
scripts/
  ingest_legacy_data.py      ingest legacy datasets
  ingest_sop_pinecone.py     ingest SOPs to Pinecone (vector DB)
  setup_security_and_view.sql SQL helper (DB view / security setup)
src/
  ui.py                      Streamlit UI (main entry for the app)
  orchestrator.py            orchestrator / coordination logic for agents/workflows
  agent_tools.py             helper utilities used by orchestration/agents
  prompts/
    system_prompt.txt        agent system prompt used by orchestration
```

How it fits together:
- The Streamlit UI (src/ui.py) provides the interactive front-end for users to query documents and interact with any orchestrated agents.
- The orchestrator (src/orchestrator.py) coordinates agent flows and uses helpers in src/agent_tools.py and the system prompt under src/prompts/.
- Ingestion scripts prepare data into data/ and (optionally) push embeddings into a vector DB (scripts/ingest_sop_pinecone.py). The docs/ folder contains instructions for setup and usage.

---

## How to run it (short path)
1. Clone the repo:
   ```
   git clone https://github.com/bharathjinka09/AI-cold-chain-logistics-FDE-Project.git
   cd AI-cold-chain-logistics-FDE-Project
   ```

2. Install dependencies:
   ```
   python -m venv .venv
   source .venv/bin/activate    # macOS / Linux
   .venv\Scripts\activate       # Windows (PowerShell/CMD)
   pip install -r requirements.txt
   ```

3. Run the Streamlit UI:
   ```
   streamlit run src/ui.py
   ```
   - If you prefer to run modules directly, inspect src/ui.py for entry checks (if __name__ == "__main__": ...).

4. Ingest data (optional)
   - Read docs/instrutions.md before running ingestion scripts.
   - Example (general pattern):
     ```
     # inspect the ingestion script for required env vars and flags
     python scripts/ingest_sop_pinecone.py --help
     python scripts/ingest_sop_pinecone.py <path-to-sop-dir-or-file> [--index <index-name>]
     ```
   - scripts/ingest_sop_pinecone.py is the Pinecone ingestion helper — check the top of the script and docs/instrutions.md for required API keys and env vars.

5. Orchestrator / agents:
   - The orchestrator is in src/orchestrator.py. Inspect the file to see how to start coordinated tasks or run unit tasks from the command line.

Notes:
- See docs/instrutions.md and the scripts themselves for exact environment variables and configuration required by Pinecone/LLM integrations and any secrets/API keys.
- The repository includes notes.pdf and docs/instrutions.md with additional design and usage information — open them for more context.

---

## Files to review first
- src/ui.py — the UI entrypoint
- src/orchestrator.py — orchestration / agent flow logic
- src/agent_tools.py — agents & helper utilities
- scripts/ingest_sop_pinecone.py — vector DB ingestion
- docs/instrutions.md — usage and setup instructions
- requirements.txt — exact Python dependencies

---

## Contributing
- Read docs/instrutions.md and run the UI locally to reproduce behavior.
- Add tests where appropriate, especially around ingestion scripts and orchestrator logic.
- Open issues or PRs describing the problem or enhancement; include steps to reproduce and relevant logs.

---

## Try asking
- "What environment variables and API keys does scripts/ingest_sop_pinecone.py require, and where should I set them?"
- "Which inputs and configuration does src/orchestrator.py expect when starting an agent flow?"
- "Can you summarize docs/instrutions.md and notes.pdf so I can quickly see the required setup and example workflows?"

---
