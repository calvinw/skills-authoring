# dolt-db-skills

This repo is for working on skills that manage the **BusMgmtBenchmarks** Dolt database — a financial data project tracking retail company financials from SEC 10-K filings and Yahoo Finance.

Skills are slash commands available through agent execution.

## Available Skills

- `/analyze-financials TICKER YEAR` — Fetches financials from SEC, Yahoo Finance, and the Dolt DB, compares them side by side, detects anomalies, and produces reconciled DB-ready values. Saves a report to `reports/`.
- `/insert-financials TICKER YEAR` — Generates a `REPLACE INTO` SQL file from the reconciled values produced by `/analyze-financials`. Writes to `extract/2026/inserts/`. Does NOT write to the database directly.

Always run `/analyze-financials` before `/insert-financials` in the same session.

## MCP Servers

The following MCP servers are pre-installed and available:

```
dolt=https://bus-mgmt-databases.mcp.mathplosion.com/mcp-dolt-database/sse
sec-10ks=https://bus-mgmt-databases.mcp.mathplosion.com/mcp-sec-10ks/sse
yfinance-10ks=https://bus-mgmt-databases.mcp.mathplosion.com/mcp-yfinance-10ks/sse
```

Check available MCPs with `/mcp` in your agent.

The target database is `calvinw/BusMgmtBenchmarks/main`.

## Setup

The environment is automatically set up on container creation. Skills are pre-installed and ready to use through agent execution with `claude.sh` or `opencode.sh`.
