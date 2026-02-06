# Lesson 1.3: Undoing Uncommitted Changes

## Why This Matters

Remember the first problem we talked about? *"I broke it and can't get it back."* This lesson shows you how Git helps solve that problem—before you even commit.

When you're connected to Git, Fabric tracks your changes. If you make a mistake, you can discard those changes and restore the last committed version with a single click.

---

## Overview

In this lesson, you will:

- Make a change to your notebook
- View uncommitted changes in Source control
- Use Undo to discard changes and restore the last committed version

**Estimated Time:** 5-10 minutes

**Prerequisites:**
- Completed Lesson 1.2
- Your Fabric workspace connected to Git
- At least one commit in your repository

---

## Make a Change to Your Notebook

Let's make a change that we'll then undo.

1. Open your Fabric workspace
2. Open the `01-hello-fabric` notebook
3. Add a new code cell at the bottom with this code:

```python
# Oops - this is a mistake!
broken_code = [1, 2, 3
print("This won't work")
```

4. Notice the change indicator appears next to your notebook in the workspace list

> 💡 **Remember:** Fabric auto-saves your work, so the change is already saved to the notebook—but it hasn't been committed to Git yet.

---

## View Uncommitted Changes

Before we undo, let's see what Fabric knows about our changes.

1. Click the **Source control** button in the toolbar
2. In the Source control panel, you'll see your notebook listed under **Changes**
3. The notebook shows as modified (not equal sign ≠)

This is Fabric telling you: "You have changes that aren't in Git yet."

---

## Undo the Change

Now let's discard this change and restore the notebook to its last committed state.

1. In the Source control panel, find your notebook in the **Changes** list
2. Select the checkbox next to your notebook
3. Check the **"I understand that workspace items may be deleted and can't be restored"** box
4. Click **Undo**
5. Click **Undo** again to confirm

> ⏳ **Wait:** Fabric will restore the file from Git. This may take a moment.

---

## Verify the Undo

1. Open your `01-hello-fabric` notebook
2. The broken code cell should be **gone**
3. Your notebook is back to the last committed version

🎉 **You just undid a mistake!**

---

## Understanding What Happened

```
┌─────────────────────────────────────────────────────────────────┐
│                         TIMELINE                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Last Commit           Your Change            After Undo        │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Working notebook  →  Added broken code  →  Back to working     │
│  (in Git)             (not committed)       (restored from Git) │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Key Points:**

1. **Undo discards uncommitted changes** - Only changes you haven't committed yet
2. **Git is your safety net** - Your last commit is always there to restore from
3. **This only works before committing** - Once you commit, you need different tools (we'll cover this in Section 4)

---

## When to Use Undo

| Scenario | Use Undo? |
|----------|-----------|
| You made changes you don't want (not committed yet) | ✅ Yes |
| You want to start fresh from the last commit | ✅ Yes |
| You already committed the changes | ❌ No—see Section 4 |
| You want to keep some changes but discard others | ⚠️ Partial—undo is all-or-nothing per item |

> 💡 **What about committed changes?** If you've already committed something and need to undo it, you'll learn how to revert commits using Pull Requests in Section 4. That approach works even after changes have been merged to your main branch.

---

## Summary

In this lesson, you:

- ✅ Made a change to your notebook
- ✅ Viewed uncommitted changes in Source control
- ✅ Used Undo to discard changes and restore from Git
- ✅ Learned the difference between uncommitted and committed changes

### The Safety Net

This is part of what we promised: **mistakes are reversible**. As long as you haven't committed yet, you can always get back to your last known good state with a single click.

---

## What's Next?

In the next section, we'll set up deployment pipelines—moving your work from development through test to production.

---

**Previous:** [Lesson 1.2: Making Your First Commit](lesson-1.2-making-your-first-commit.md)  
**Next:** [Lesson 2.1: Setting Up a Deployment Pipeline](../section-02-deployment-pipelines/lesson-2.1-setting-up-a-deployment-pipeline.md)
