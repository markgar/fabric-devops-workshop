# Lesson 2.6: Adding a Test Environment

## Overview

So far, we've used a simple two-stage pipeline: **Dev → Prod**. But you've probably seen pipelines with a **Test** (or "QA" or "Staging") environment in the middle.

This lesson explains when and why you might add one—and when you shouldn't.

**Estimated Time:** 5 minutes (reading only)

---

## Why Add a Test Environment?

A test environment gives other people a chance to **review your work before it goes to production**.

| Who | Why They'd Use Test |
|-----|---------------------|
| Business users | Preview reports before they're live |
| QA team | Validate data and logic |
| Managers / stakeholders | Sign off before release |
| Other developers | Review your changes without pulling code locally |

In a Test environment, reviewers can interact with your notebooks, reports, and pipelines in a realistic setting—without any risk to production.

---

## The Three-Stage Pattern

```
┌─────────┐      ┌─────────┐      ┌─────────┐
│   Dev   │  →   │  Test   │  →   │  Prod   │
└─────────┘      └─────────┘      └─────────┘
     ↑                ↑                ↑
  You work        Others review    Users see
    here              here            this
```

This is a **very common pattern**—you'll see it in most enterprise DevOps setups. The idea is straightforward:

1. **Dev:** Where you build and experiment
2. **Test:** Where others validate your work
3. **Prod:** Where real users access it

---

## When to Add Test

Add a Test environment when:

- ✅ Multiple people need to review changes before production
- ✅ You have a formal approval or sign-off process
- ✅ Business users want to preview before go-live
- ✅ You're working on a team and need a shared "staging" area

---

## When NOT to Add Test

Here's the key point: **only make your DevOps processes as complicated as needed.**

Skip the Test environment when:

- ❌ You're the only person working on the project
- ❌ You can validate everything yourself in Dev
- ❌ Adding another environment creates overhead without real benefit
- ❌ You're just learning or prototyping

Every environment you add means:
- Another workspace to manage
- Another stage in the pipeline to monitor
- More complexity to maintain

**Complexity has a cost.** If a simpler process works for your situation, use it.

---

## The Right Amount of Process

There's no universal answer. The right setup depends on:

| Factor | Simpler (Dev → Prod) | More Stages (Dev → Test → Prod) |
|--------|---------------------|--------------------------------|
| Team size | Solo or small team | Larger team with reviewers |
| Risk tolerance | Low-stakes projects | Business-critical reports |
| Approval needs | Informal | Formal sign-off required |
| Iteration speed | Fast experiments | Controlled releases |

**Start simple.** You can always add a Test environment later if you need it. It's harder to remove complexity once it's established.

---

## How to Add Test (If You Need It)

If you decide you need a Test environment, you'll need to create a new pipeline — remember from Lesson 2.1 that the number of stages is permanent after creation.

1. Create a new workspace (e.g., `FabricDevOps-Workshop-Test`)
2. Create a new deployment pipeline with three stages: Dev, Test, and Prod
3. Assign your workspaces to each stage
4. Deploy: Dev → Test → Prod

The mechanics are the same as what you've already learned—just with an extra stage.

---

## Summary

- **Test environments let others review your work** before it reaches production
- This is a **common and useful pattern** in team settings
- But **don't add complexity you don't need**—start with Dev → Prod and expand if required
- The best DevOps process is the **simplest one that works for your situation**

---

**Previous:** [Lesson 2.5: Practice - Tag and Deploy Again](lesson-2.5-practice-tag-and-deploy.md)  
**Next:** [Lesson 3.1: Adding a Lakehouse to Your Notebook](../section-03-deployment-rules/lesson-3.1-adding-a-lakehouse-to-your-notebook.md)
