# Multi-Agent-System-using-LangGraph-MCP-Supervisor-Guardrails-HITL

## Database availability

The app uses the configured PostgreSQL database for durable LangGraph
checkpoints. If PostgreSQL is temporarily unreachable, the app logs a warning
and starts with in-memory checkpoints so it can still serve requests. In this
fallback mode, pending approvals and other checkpoints are lost when the
application restarts. Restore the PostgreSQL connection to resume durable
checkpointing.