# Recover Accidentally Modified or Deleted File Using Git

## Overview

If a file is accidentally modified, deleted, or important content is removed, Git allows you to recover the previous version of the file from the commit history.

This is useful when working with documentation files, code, or configuration files where accidental changes may occur.

---

## Scenario

Example:

- File: `Opensource/Proxmox.md`
- Accidentally removed some commands or documentation content in Obsidian.
- Changes were committed and pushed to Git.

Example commit:

```
git commit -m "Update Proxmox documentation"git push
```

The incorrect changes are now saved in the repository, but Git still maintains the previous versions.

---

# Step 1: Check Commit History

View previous commits:

```
git log --oneline
```

Example output:

```
a1b2c3d Update Proxmox documentatione4f5g6h Add initial Proxmox guide
```

- `a1b2c3d` → Latest commit containing the accidental change
- `e4f5g6h` → Previous working version

---

# Step 2: Review Changes

Check what was changed in the latest commit:

```
git show
```

or:

```
git show <commit-id>
```

Example:

```
git show a1b2c3d
```

Git will display:

- Added lines with `+`
- Removed lines with `-`

Example:

```
- apt update- apt upgrade+ apt update
```

This helps identify accidentally removed content.

---

# Step 3: Restore Previous File Version

Restore the file from the previous working commit:

```
git checkout <previous-commit-id> -- Opensource/Proxmox.md
```

Example:

```
git checkout e4f5g6h -- Opensource/Proxmox.md
```

This restores only the selected file without affecting other files.

---

# Step 4: Verify Restored Content

Check the restored changes:

```
git diff
```

Confirm that the missing commands or content are available again.

---

# Step 5: Commit the Recovery

Stage the restored file:

```
git add Opensource/Proxmox.md
```

Create a recovery commit:

```
git commit -m "Restore missing Proxmox documentation steps"
```

Push the changes:

```
git push
```

---

# Quick Recovery Method (Before Commit)

If you notice accidental changes before committing:

Check changes:

```
git diff
```

Discard changes:

```
git restore Opensource/Proxmox.md
```

This will restore the file to the last committed version.

---

# Best Practice Before Every Commit

Always review your changes before committing:

```
git status
```

Check detailed changes:

```
git diff
```

Then commit:

```
git add Opensource/Proxmox.mdgit commit -m "Update Proxmox documentation"git push
```

---

## Summary

|Task|Command|
|---|---|
|View commits|`git log --oneline`|
|View changes|`git show <commit-id>`|
|Restore old file|`git checkout <commit-id> -- <file>`|
|Check changes|`git diff`|
|Stage file|`git add <file>`|
|Commit recovery|`git commit -m "message"`|
|Push changes|`git push`|