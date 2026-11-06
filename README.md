# Multi-Agent-System-using-LangGraph-MCP-Supervisor-Guardrails-HITL

## Database availability

The app uses the configured PostgreSQL database for durable LangGraph
checkpoints. If PostgreSQL is temporarily unreachable, the app logs a warning
and starts with in-memory checkpoints so it can still serve requests. In this
fallback mode, pending approvals and other checkpoints are lost when the
application restarts. Restore the PostgreSQL connection to resume durable
checkpointing.

The PostgreSQL checkpointer uses a connection pool that validates connections
before reuse, allowing it to recover from dropped database connections. The
Groq requests throughout the workflow limit prompt context and generated output
to reduce the chance of exceeding the model's token-per-minute quota. Supervisor
routing has a larger output budget for its JSON response, and weather lookup
returns a clear unavailable result instead of failing the trip when no
destination can be identified.