# Zenavo skills for Claude Code

A [Claude Code](https://claude.com/claude-code) plugin for [Zenavo](https://zenavo.app): deploy, debug, roll back
and configure your projects by asking, with an API key that can do no more than you allow.

## Install

1. Install and sign in to [zenavo-mcp](https://github.com/Zenavo-App/zenavo-mcp), the MCP server these skills use:

   ```sh
   zenavo-mcp login
   ```

   When you approve in the console, choose **Deploy** (or **Read only**) and limit the key to the projects
   Claude should work on.

2. Add the plugin:

   ```sh
   claude plugin marketplace add Zenavo-App/zenavo-skills
   claude plugin install zenavo@zenavo
   ```

The plugin starts `zenavo-mcp` itself; no key goes in any Claude Code setting.

## Skills

| Skill | Use it to |
| --- | --- |
| `zenavo-deploy` | Deploy a project or service, follow the job, and check it came up |
| `zenavo-debug` | Find out why a deploy failed or a service crashes, from status, job output and logs |
| `zenavo-rollback` | Go back to an earlier working deployment |
| `zenavo-env` | Add, change or remove environment variables without the values entering the conversation where possible |
| `zenavo-setup` | Install and sign in to zenavo-mcp when the tools are missing |

Claude asks before anything that changes what runs: deploys, rollbacks, restarts and variable changes. Configuration
values are never shown to it. Billing, servers and team members stay in the Zenavo console.

## License

[Apache License 2.0](LICENSE)
