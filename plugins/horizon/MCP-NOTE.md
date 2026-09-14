The MCP server is declared in `.mcp.json`, not inline in `plugin.json`.

Both forms pass `claude plugin validate`. Only the `.mcp.json` form is loaded as
a component: with the inline form, `claude plugin details` reports "MCP servers
(0)" and the skills would fire with no Horizon tools behind them. Verified on
Claude Code 2.1.270, 2026-09-14. Keep it in `.mcp.json`.
