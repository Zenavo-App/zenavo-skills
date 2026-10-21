---
name: zenavo-env
description: Add, change or remove environment variables of a Zenavo service, and apply them. Use when the user asks to set a variable, add a secret or API key, change configuration, or a deploy is blocked by a missing variable.
---

# Environment variables on Zenavo

Values are never shown to you: `list_env` returns names, and `set_env` does not echo what it stored. Keep it that way.

1. **Look first.** Call `list_env` for the service to see which variables exist. A value like `${POSTGRES_HOST}` is
   shown because it only references another variable.
2. **Get the value from the user, not by guessing.** For passwords, API keys and other secrets, recommend that the
   user sets them in the Zenavo console (the service's **Variable** tab) so the value never passes through this
   conversation; then you only need to deploy. If they prefer to give the value here, use exactly what they give.
   Never invent secrets, and never copy values out of logs or files into a variable without the user's say-so.
   For a value that refers to another service, use a reference like `${POSTGRES_HOST}` instead of copying it.
3. **Confirm.** Say which variable you will set on which service, and that it takes effect on the next deploy.
4. **Change it.** Call `set_env` (or `unset_env`). Pass `deploy: true` if the user wants it applied now; otherwise
   offer to deploy with the zenavo-deploy skill.
5. **Never repeat a secret value** in your replies, commit it to a repository, or write it to a file.
