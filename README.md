# YNAB Gmail Import

Project to test importing YNAB transactions from gmail for vendors like Amazon, Target, and Apple. This project uses two open source MCP projects: 

 - google_workspace_mcp - https://github.com/taylorwilsdon/google_workspace_mcp
 - ynab-mcp-server - https://github.com/calebl/ynab-mcp-server

# Install

1. Install WSL2 (Windows only)
2. Install Claude Code
3. Clone google_workspace_mcp - https://github.com/taylorwilsdon/google_workspace_mcp
    1. Use instructions to configure http single user server
4. Clone ynab-mcp-server - https://github.com/calebl/ynab-mcp-server
    1. Use instructions to build the project
5. Clone this project: ynab_import_test
    1. Configure the MCPs per the example below by editing: ```~/.claude.json ```
    2. Export your ynab plan to a csv and save it to the directory as "plan.csv"
    3. Use the prompt below to have Claude update the plan.csv file with category IDs from YNAB

## Example MCP Config

```

      "mcpServers": {
        "google-workspace": {
          "type": "http",
          "url": "http://localhost:8000/mcp",
          "env": {}
        },
        "ynab-mcp-server": {
          "command": "node",
          "args": [
            "~/ynab-mcp-server/dist/index.js"
          ],
          "cwd": "~/ynab-mcp-server",
          "env": {
            "YNAB_API_TOKEN": "xxxxxxxxxxxxxxxxx",
            "YNAB_BUDGET_ID": "xxxxxxxxxxxxxxxx"
          }
        }
      },

```

## Prompt to update your plan.csv data with category IDs

```
Add a data column in plan.csv file named "Category ID" and add a YNAB Category ID for each category using the YNAB MCP.
```

# Usage

## Start Google MCP Server 

```
cd ~/google_workspace_mcp
source ~/google1/.google_workspace_env
uv run main.py --tools gmail --tool-tier extended  --transport streamable-http
```

## Run Claude Command

Using Interactive Claude Code

```
cd ~/ynab_import_test
claude
/nabg
```

Command Line

```
cd ~/ynab_import_test
claude -p "/nabg" --dangerously-skip-permissions
```



