# Lesson 4.2: Branching Strategy

## Why Feature Branches?

In the last lesson, we identified a problem: Fabric workspaces are shared, not local. If everyone works in the same Dev workspace, you'll overwrite each other's changes and deploy incomplete work.

Feature branches solve this. Each developer works on their own branch, in their own workspace—completely isolated until their work is ready.

---

## Overview

In this lesson, you will learn:

- What a branch is and how it works
- The lifecycle of a feature branch
- Why we never commit directly to `main`
- How to protect `main` with branch policies

**Estimated Time:** 10 minutes (reading only)

**Prerequisites:**
- Completed Lesson 4.1

---

## What Is a Branch?

A branch is a parallel copy of your code where you can make changes without affecting anyone else.

```
main         ●────●────●────●────●────●
                   \              ↑
feature-add-report  ●────●────●──┘
                    (your work)  (merge)
```

- **`main`** is the long-living branch—it always exists
- **Feature branches** are short-lived—they exist only while you're working on something
- When your feature is complete, you **merge** it back to `main`

A "feature" can be anything—adding a visual to a report, adding a column to a semantic model, creating a new notebook, or fixing a bug. If it's a unit of work, it gets a branch.

Think of it like this:

| Branch | Purpose | Lifespan |
|--------|---------|----------|
| `main` | Stable, merged code ready for deployment | Forever |
| `feature-*` | Your in-progress work | Days to weeks |

---

## The Golden Rule: Never Commit to Main

Here's the rule that makes everything work:

> **Never commit directly to `main`. Always use a feature branch.**

Why? Because `main` represents code that is:
- ✅ Complete (not half-finished)
- ✅ Reviewed (someone else looked at it)
- ✅ Ready to deploy (won't break production)

If developers commit directly to `main`, you lose all of this. Someone's incomplete work could end up in production. Someone could overwrite someone else's changes. Chaos.

---

## The Feature Branch Lifecycle

Here's how a feature branch lives and dies:

```
┌─────────────────────────────────────────────────────────────────────┐
│                    FEATURE BRANCH LIFECYCLE                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   1. CREATE          2. WORK              3. MERGE                  │
│   ┌─────────┐       ┌─────────┐          ┌─────────┐               │
│   │ Branch  │       │ Develop │          │ Pull    │               │
│   │ from    │──────►│ & Test  │─────────►│ Request │───► main      │
│   │ main    │       │         │          │         │               │
│   └─────────┘       └─────────┘          └─────────┘               │
│                                                                     │
│   Create branch     Work in your          Create PR, get review,   │
│   & workspace       own workspace         merge, delete branch     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 1. Create a Branch

When you start new work:
- Create a new branch from `main` (e.g., `feature-add-sales-report`)
- Create a new Fabric workspace connected to that branch
- This is your private development environment

### 2. Work in Your Branch

While developing:
- Make changes in your workspace
- Commit to your branch (not `main`!)
- Test, iterate, repeat
- Nobody else is affected by your work

### 3. Merge via Pull Request

When your feature is complete:
- Create a **pull request** (PR) to merge your branch into `main`
- Teammates review your changes
- Once approved, the PR merges your code into `main`
- Delete your branch and workspace—they're no longer needed

---

## How This Maps to Fabric Workspaces

Here's the full picture:

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   YOUR WORKSPACE              TEAM WORKSPACES                       │
│   (Your branch)               (main branch)                         │
│                                                                     │
│   ┌─────────────────┐        ┌─────────────────┐                   │
│   │ Alice-Dev       │        │ Dev             │                   │
│   │ (feature-x)     │───PR──►│ (main)          │                   │
│   └─────────────────┘        └────────┬────────┘                   │
│                                       │                             │
│   ┌─────────────────┐                 │ Deploy                      │
│   │ Bob-Dev         │                 ▼                             │
│   │ (feature-y)     │───PR──►┌─────────────────┐                   │
│   └─────────────────┘        │ Prod            │                   │
│                              │ (main)          │                   │
│                              └─────────────────┘                   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

| Workspace | Connected To | Purpose |
|-----------|--------------|---------|
| `Alice-Dev` | `feature-x` branch | Alice's private development |
| `Bob-Dev` | `feature-y` branch | Bob's private development |
| `Dev` | `main` branch | Merged code, ready for testing |
| `Prod` | `main` branch (via pipeline) | Production |

The **Dev workspace** bound to `main` isn't where developers work—it's where finished code lands after merging. Think of it as the staging area for merged features.

---

## Protecting Main: Branch Policies

To enforce "never commit to main," we configure **branch policies** in Git. These are rules that prevent direct commits and require pull requests.

### What Branch Policies Do

| Policy | What It Does |
|--------|--------------|
| **Require pull request** | Blocks direct commits to `main` |
| **Require reviewers** | Someone must approve the PR before merging |
| **Require linked work items** | PR must reference a task or bug (optional) |
| **Build validation** | Run automated checks before allowing merge (optional) |

We'll configure these in the next lesson.

---

## Optional: Make Dev Workspace Read-Only

As an extra safeguard, you can make the Dev workspace **read-only** for developers:

- Developers can view items but not edit them
- Only the Git sync (from merged PRs) updates the workspace
- Prevents anyone from accidentally making changes outside the Git flow

This is optional but recommended for larger teams.

---

## Summary

| Concept | Description |
|---------|-------------|
| **`main` branch** | Long-living branch with stable, merged code |
| **Feature branch** | Short-lived branch for your in-progress work |
| **Pull request** | How you merge your branch into `main` |
| **Branch policy** | Rules that prevent direct commits to `main` |

### Key Takeaways

1. **Never commit to `main`** — Always use feature branches
2. **Each developer gets their own workspace + branch** — This is your private inner loop
3. **The Dev workspace shows merged code** — It's bound to `main`, not for active development
4. **Pull requests are the gateway to `main`** — They ensure review and completeness
5. **Branch policies enforce the rules** — Git prevents accidental direct commits

---

**Previous:** [Lesson 4.1: Inner Loop and Outer Loop](lesson-4.1-inner-loop-outer-loop.md)  
**Next:** [Lesson 4.3: Configuring Branch Policies](lesson-4.3-configuring-branch-policies.md)
