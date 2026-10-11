# Odoo upstream sync

This branch contains the automation for the 0yik/odoo fork.
Keep sync as the GitHub default branch so scheduled workflows run.
Use 20.0 as your development checkout, or switch to another Odoo branch.

The workflow runs every day at 07:15 Asia/Jakarta (00:15 UTC).
You can also start it from Actions → Sync upstream → Run workflow.
GitHub schedules can be delayed.

The workflow updates only master, 20.0, 19.0, and 18.0 from odoo/odoo.
It uses the built-in GitHub token with contents: write and does not
download repository history. Each update is a fast-forward, keeping
the branch at the upstream commit. If a branch diverges, its job fails
rather than discarding your commits.

The workflow does not update your local checkout. To update locally:

```sh
git fetch origin --depth=1 --no-tags
git switch 20.0
git merge --ff-only origin/20.0
```

Public repositories can have scheduled workflows disabled after
60 days without repository activity. If that happens, re-enable
Sync upstream in the Actions tab.
