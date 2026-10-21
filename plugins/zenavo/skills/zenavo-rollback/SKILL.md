---
name: zenavo-rollback
description: Roll a Zenavo service or project back to an earlier working deployment. Use when the user wants to undo a deploy, go back to the previous version, or restore service quickly after a bad release.
---

# Roll back on Zenavo

1. **See the history.** Call `list_deployments` for the affected service. The entry with `current: true` is what
   runs now. Pick the newest earlier entry with status `succeeded`, unless the user named one.
2. **Confirm.** Tell the user which deployment runs now, which one you will return to (its ID, time and who
   deployed it), and whether this rolls back one service or the whole project. Mention that configuration changes
   made since then are not part of a rollback. Wait for a clear yes.
3. **Roll back.** Call `rollback` with the project, the service (omit it for the whole project) and the deployment ID.
4. **Follow and verify.** Call `get_job` with `wait_seconds: 60` until it finishes, then `get_project` to check
   the service is ready and not restarting.
5. **Afterwards.** Suggest finding the cause with the zenavo-debug skill, so the fix can be deployed again.
