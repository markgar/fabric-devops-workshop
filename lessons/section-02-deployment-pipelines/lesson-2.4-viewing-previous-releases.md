# Lesson 2.4: Viewing Previous Releases with Tags

## Why This Matters

Development keeps moving forward, but production stays at the deployed version. After a few days of work, how do you know what's actually running in production vs. what's only in dev?

Tags let you "go back in time" and see exactly what was deployed—even after you've made many more commits.

---

## Overview

Now that you've deployed to production and tagged your release, let's see how tags help you answer the question: **"What exactly is in production right now?"

In this lesson, you will:

- Make a new change in development (simulating ongoing work)
- Use your tag in GitHub to view the code as it was when you deployed
- Understand how tags let you "go back in time"

**Estimated Time:** 10 minutes

**Prerequisites:**
- Completed Lesson 2.3 (deployed to production)
- Your release tag created in Lesson 2.2

---

## Make a New Change

Let's simulate what happens in real life: you deployed to production, and now you're continuing to work on new features in development.

1. Go to your **development** workspace (`FabricDevOps-Workshop-Dev`)
2. Open your `01-hello-fabric` notebook
3. Add a new code cell with the following content:

```python
# New feature in development - not yet deployed
print("This is a new feature!")
print("It's only in dev - production doesn't have this yet.")
```

4. Save the notebook (Fabric auto-saves, but **Ctrl/Cmd + S** works too)
5. Open the **Source control** panel
6. Select the modified notebook
7. Enter a commit message:
   ```
   Add new feature (in development)
   ```
8. Click **Commit**

Now your development workspace is **ahead** of production. This is normal—dev always has the latest work, while prod has only what's been deployed.

---

## View the Deployed Version in GitHub

Here's where tags become valuable. Your `main` branch now has the new feature, but production doesn't. How do you see what's actually in production?

**Use the tag.**

1. Open [https://github.com](https://github.com)
2. Go to your repository (e.g., `fabric-devops-workshop`)
3. Make sure you're viewing the `main` branch (default)
4. Click on the folder for your notebook (e.g., `01-hello-fabric.Notebook`)
   - Fabric items are stored in folders named `itemname.ItemType`
5. Open `notebook-content.py` — this is where the Python code lives
6. Notice it includes the **new feature** code you just added

   This is the latest code—but it's NOT what's in production.

7. Click on the **branch dropdown** (shows `main`)
8. Click on the **Tags** tab
9. Select your deployment tag (e.g., `v1`)

   The page will refresh, and now you're viewing the repository **as it was when you created that tag**.

10. Navigate to your notebook folder and file again
11. Notice the **new feature code is NOT there**

This is exactly what's in production—the code as it was at deployment time.

---

## Why This Matters

### Scenario: "Something's broken in production!"

Imagine a user reports a bug. You need to see exactly what code is running in production to debug it.

- ❌ **Without tags:** You'd have to guess which commit was deployed, or dig through deployment history
- ✅ **With tags:** Click the tag, see exactly what's deployed

### Scenario: "What changed since the last deployment?"

You want to review all changes before the next deployment.

1. In GitHub, go to your tag
2. Click **Compare** to compare the tag with `main`
3. See all the commits and changes since that deployment

### Scenario: "We need to roll back"

Something went wrong and you need to restore the previous version.

1. You know exactly what version worked (the tag)
2. You can deploy from that specific point
3. Or revert changes back to that tagged state

---

## The Big Picture

Here's what your repository looks like now:

```
                                         main branch (latest)
                                                │
                                                ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Initial    │    │  Deployed to │    │ New feature  │
│   notebook   │───►│  production  │───►│ (dev only)   │
│              │    │              │    │              │
└──────────────┘    └──────────────┘    └──────────────┘
                           ▲
                           │
                          v1
                        (tag)
```

- **main branch** always points to the latest commit
- **Tags** are permanent markers that don't move
- You can always view the code at any tag, regardless of new commits

---

## Summary

In this lesson, you:

- ✅ Made a new commit after deploying (simulating ongoing development)
- ✅ Used a tag to view the repository at the deployment point
- ✅ Saw how tags help you track what's actually in production

### Key Concepts

1. **Tags don't move** - Unlike branches, tags stay at the commit where you created them
2. **View any version** - Switch to a tag to see the code as it was at that point
3. **Compare versions** - Use tags to see what changed between deployments

---

## What's Next?

You've now completed the deployment pipelines section! You can:

- Deploy updates by tagging and deploying again
- Always know what's in production by checking the tag
- Compare changes between deployments

In the next section, we'll explore **feature branches**—how to work on new features without affecting the main codebase or your teammates.

---

**Previous:** [Lesson 2.3: Deploying to Production](lesson-2.3-deploying-to-production.md)  
**Next:** [Lesson 2.5: Practice - Tag and Deploy Again](lesson-2.5-practice-tag-and-deploy.md)
