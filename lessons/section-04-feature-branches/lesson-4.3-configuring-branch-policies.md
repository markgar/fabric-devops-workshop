# Lesson 4.3: Configuring Branch Policies

## Why Branch Policies?

In the last lesson, we established the golden rule: never commit directly to `main`. But rules only work if they're enforced. Without enforcement, someone will inevitably forget (or ignore) the rule and push directly to `main`.

Branch policies are Git's way of enforcing the rules automatically. Configure them once, and Git will block any direct commits to `main`—no exceptions.

---

## Overview

In this lesson, you will:

- Create a branch protection rule in GitHub
- Test that direct commits are blocked
- Understand what happens when you try to push to a protected branch

**Estimated Time:** 10 minutes

**Prerequisites:**
- Completed Lesson 4.2
- A GitHub repository connected to your Fabric workspace (from Section 1)

---

## Create a Branch Protection Rule

Let's configure GitHub to require pull requests for any changes to `main`.

1. Go to [GitHub](https://github.com) and open your repository
2. Click **Settings** (tab at the top of the repo)
3. In the left sidebar, click **Branches** (under "Code and automation")
4. Under "Branch protection rules," click **Add branch ruleset**

   > 💡 **Note:** GitHub has two systems: the older "Branch protection rules" and the newer "Branch rulesets." Either works, but rulesets are the modern approach.

5. Give your ruleset a name: `Protect main branch`
6. Set **Enforcement status** to **Active**

---

## Configure the Target Branch

1. Under **Target branches**, click **Add target**
2. Select **Include default branch**
   
   This applies the rule to your `main` branch.

---

## Enable the Pull Request Requirement

1. Scroll down to **Branch rules**
2. Check **Require a pull request before merging**

   This is the key setting—it blocks direct commits to `main`.

3. Leave other options unchecked for now (we're keeping it simple)
4. Click **Create** at the bottom of the page

> ✅ Your `main` branch is now protected! Any attempt to push directly to `main` will be rejected.

---

## Test the Protection

Let's verify that the protection works.

1. Go to your **Development** workspace in Fabric
2. Make a small change to your notebook (add a comment or blank line)
3. Click **Source control**
4. Try to commit the change

You should see an error message indicating that direct pushes to `main` are not allowed. The exact message varies, but it will mention that a pull request is required.

> ✅ **This is exactly what we want!** The branch policy is blocking direct commits.

Discard your test change:

1. Use the **Source control** panel to undo your uncommitted changes (remember [Lesson 1.3](../section-01-git-basics/lesson-1.3-undoing-uncommitted-changes.md)? 😊)

---

## What This Means for Your Workflow

With branch protection enabled, here's what changes:

| Before | After |
|--------|-------|
| Make changes in Dev workspace | Make changes in your **own** workspace |
| Commit directly to `main` | Commit to a **feature branch** |
| Changes go straight to the repo | Changes require a **pull request** |

### The New Workflow

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   1. Create feature branch                                          │
│   2. Create workspace connected to that branch                      │
│   3. Make changes, commit to your branch                            │
│   4. Create pull request to merge into main                         │
│   5. After merge, Dev workspace syncs automatically                 │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

We'll walk through this workflow hands-on in the next lesson.

---

## Optional: Additional Protection Settings

For this workshop, we're keeping it simple with just the PR requirement. But for real projects, consider these additional settings:

| Setting | What It Does | When to Use |
|---------|--------------|-------------|
| **Require approvals** | Someone must approve the PR before merging | Teams with 2+ developers |
| **Dismiss stale approvals** | Re-require approval if new commits are pushed | When approval integrity matters |
| **Require status checks** | Automated tests must pass before merging | When you have CI/CD pipelines |
| **Require linear history** | Prevents merge commits, keeps history clean | When you prefer squash merges |

You can always come back and enable these later.

---

## Summary

In this lesson, you:

- ✅ Created a branch protection rule in GitHub
- ✅ Verified that direct commits to `main` are blocked
- ✅ Learned what the new workflow looks like

### Key Takeaways

1. **Branch protection enforces the rules** — No more accidental commits to `main`
2. **One setting does the heavy lifting** — "Require a pull request before merging"
3. **The Dev workspace is now read-only (effectively)** — You can't commit from it anymore
4. **You need a feature branch to make changes** — Which we'll create next

---

**Previous:** [Lesson 4.2: Branching Strategy](lesson-4.2-branching-strategy.md)  
**Next:** [Lesson 4.4: Creating a Feature Branch](lesson-4.4-creating-a-feature-branch.md)
