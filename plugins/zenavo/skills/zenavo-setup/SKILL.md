---
name: zenavo-setup
description: Set up the Zenavo tools when they are missing or not signed in, e.g. the zenavo MCP server fails to start, its tools are absent, or a Zenavo tool answers "not signed in". Use before any other Zenavo skill if the tools do not work.
---

# Set up Zenavo for Claude Code

The Zenavo skills use the `zenavo` MCP server, which this plugin starts by running `zenavo-mcp`. It needs to be
installed and signed in once per computer. You help the user do that; you never sign in for them.

## 1. Is it installed?

Run `zenavo-mcp version`. If the command is missing, tell the user to install it from
https://github.com/Zenavo-App/zenavo-mcp/releases (the README there shows how to check the download), or with Go:
`go install github.com/Zenavo-App/zenavo-mcp/cmd/zenavo-mcp@latest`. Do not download or install binaries yourself
unless the user asks you to, and then only from that releases page, checking `SHA256SUMS`.

## 2. Is it signed in?

Run `zenavo-mcp status`. If it says "Not signed in", ask the user to run this in their own terminal:

```sh
zenavo-mcp login
```

Explain what happens: a code appears, the Zenavo console opens, they check the code and approve. On that page
they choose the permission (Read only, or Deploy to also deploy and change configuration) and should limit the key to
the projects you will work on. Never run `zenavo-mcp login` yourself and never ask the user to paste an API key into
the conversation.

## 3. Reconnect

After installing or signing in, the user may need to restart Claude Code (or run `/mcp` to reconnect the `zenavo`
server). Then call the `whoami` tool to confirm the account and permission, and continue with what they asked.
