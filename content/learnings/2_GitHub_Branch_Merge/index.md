---
title: "Branch Merge - GitHub"
date: 2025-12-03
description: "Add description"
summary: "GitHub"
tags: []
---

Here is a flow for merging dev branch into main.

#### Step 1. Run
```bash
git switch main   # Switch to the main branch
git pull          # Update main (local branch) with the newest code from the remote repository
git merge dev     # Merge the dev branch into main
```

#### Step 2. Conflicts? ❌ NO

Skip to `Step 4`


#### Step 3. Conflicts? ✅ YES 

Resolve
```bash
git status   # Check which files have conflicts
```

You will see conflicted files (e.g. `src/app.js`).

Open the file (e.g. `src/app.js`) you will see something like:
```bash
<<<<<<< HEAD
content from main branch
=======
content from dev branch
>>>>>>> dev
```
Replace the entire block above with `the final version you want` (this can be main version, dev version, or a custom combined version).

Then run
```bash
git add src/app.js                                  # Stage the resolved file
git commit -m "Resolve merge conflicts in app.js"   # Commit the fix
```

#### Step 4. Push the merged result
```bash
git push
```

#### Step 5. (Optional) Clean up the dev branch
```bash
git branch -d dev.             # Delete the local dev branch
git push origin --delete dev   # Delete the remote dev branch
```