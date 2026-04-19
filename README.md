# dolt-db-skills

This repo is for working on skills that manage the **BusMgmtBenchmarks** Dolt database — a financial data project tracking retail company financials from SEC 10-K filings and Yahoo Finance.

Skills are slash commands (e.g., `/analyze-financials`) available through AI tool agents.

## Available Skills

### `/analyze-financials TICKER YEAR`

**Purpose:** Fetch, compare, and reconcile financial data for a retail company across multiple sources (SEC 10-K, Yahoo Finance, and Dolt DB), then produce database-ready reconciled values.

**What it does:**
1. Looks up company metadata (CIK, display name) in the Dolt database
2. Fetches income statements and balance sheets from SEC 10-K filings and Yahoo Finance in parallel
3. Extracts 13 standard financial fields (Revenue, COGS, Gross Margin, SGA, Operating Profit, Net Profit, Inventory, Current Assets, Total Assets, Current Liabilities, Liabilities, Total Shareholder Equity, Total Liabilities & SE)
4. Runs automated anomaly detection (SGA composite rules, balance sheet mismatches, restatement checks)
5. Presents a side-by-side comparison table showing differences across sources
6. Recommends reconciled values with source attribution
7. Generates and saves a markdown report to `reports/{TICKER}-{YEAR}.md`

**Usage:** `/analyze-financials TRR 2024`

### `/insert-financials TICKER YEAR`

**Purpose:** Generate a SQL `REPLACE INTO` file containing reconciled financial data from `/analyze-financials`. This skill does NOT connect to or modify the database — it writes a `.sql` file that you apply manually.

**What it does:**
1. Collects reconciled values and metadata from the prior `/analyze-financials` run
2. Constructs a `REPLACE INTO financials` SQL statement with all 13 fields
3. Writes the SQL to `extract/2026/inserts/{TICKER}_{YEAR}_insert.sql`
4. Provides instructions for applying the SQL to your local Dolt clone

**Usage:** `/insert-financials TRR 2024` (after running `/analyze-financials TRR 2024` in the same session)

**Workflow:** Always run `/analyze-financials` first, review the analysis and reconciled values, then run `/insert-financials` to generate the insert file.

## Starting Agents

Start an AI agent with permissive tool access using:

```bash
claude.sh      # Starts Claude agent
opencode.sh    # Starts OpenCode agent
```

These scripts invoke the agent with access to Dolt database tools, financial data tools (SEC 10-K, Yahoo Finance), and the installed skills for analyzing and reconciling financial data.

## MCP Servers

The Dolt MCP server is configured in `configs/mcp-servers.conf`:

```
dolt=https://bus-mgmt-databases.mcp.mathplosion.com/mcp-dolt-database/sse
sec-10ks=https://bus-mgmt-databases.mcp.mathplosion.com/mcp-sec-10ks/sse
yfinance-10ks=https://bus-mgmt-databases.mcp.mathplosion.com/mcp-yfinance-10ks/sse
```

Target database: `calvinw/BusMgmtBenchmarks/main`
