## README 📖

### What this notebook contains
- Part 1: Agentic transport query workflow for Singapore public transport (LTA DataMall + context enrichment).
- Part 2: Simulation of 10 diverse user queries with captured agent responses.

### Setup
1. Create and activate a local virtual environment.
2. Set environment variables:
   - `LTA_ACCOUNT_KEY`
   - `GROQ_API_KEY`
3. Open the notebook and run all cells top-to-bottom.

### Expected output
- Part 1 cells show successful agent workflow execution.
- Part 2 displays a styled table with exactly 10 user simulations and responses.

### Design notes
- Agent uses tool-calling style orchestration with deterministic fallback.
- Context constraints included: weather, traffic incidents, time-of-day peak logic, and public holiday signal.
- LLM is used for response synthesis only; transport/tool outputs remain grounded in API results.

### Assumptions
- LTA API key has access to required dynamic endpoints.
- Network/API limits may affect live responses; fallback behavior is expected and documented.

### Deployment approach (real-world)
- Package as a stateless API service (FastAPI) behind a scheduler/cache layer.
- Add observability (request logs, latency, fallback rate, API error rate).
- Store secrets in a managed secret store; never commit `.env`.
- Add rate limiting, retries, and circuit breakers for external APIs.
