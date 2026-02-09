# Lesson 2.2: Tagging Releases

## Why Tag Releases?

Tags solve a common problem: **"What exactly is in production right now?"**

Without tags, you'd have to remember which commit was deployed, or dig through deployment history to figure it out. With tags, you have a clear label marking exactly what's running in production.

---

## Overview

Before deploying to production, it's a good practice to **tag** your commit in Git. A tag marks a specific point in your history—like putting a bookmark that says "this is version 1 of what we released out of dev."

In environments with Dev → Test → Prod stages, tags mark your **release candidates**—the versions that moved out of development and toward production. This way you always know which release went through your pipeline and when.

In this lesson, you will:

- Understand why tagging releases matters
- Create a tag in GitHub for your current commit
- Learn tagging conventions

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lesson 2.1 (deployment pipeline set up)
- Your notebook committed to Git

---

### Benefits of Tagging

| Benefit | Description |
|---------|-------------|
| **Clear markers** | Know exactly what code is in each environment |
| **Easy rollback** | Need to go back? Deploy the tagged version |
| **Release history** | See all your production releases at a glance |
| **Communication** | Tell your team "we deployed v11" instead of "we deployed commit a3f7b2c" |

---

## A Note on Naming Conventions

There are many ways to name your releases:
- **Semantic versioning:** `v1.0.0`, `v1.1.0`, `v2.0.0` (major.minor.patch)
- **Date-based:** `prod-2025-01-15`, `release-2025-01-22`
- **Simple version numbers:** `v1`, `v2`, `v3`

Each has its place. Semantic versioning is great for products with formal release cycles where you need to communicate breaking changes. Date-based tags make it easy to find what was live on a specific day.

For this workshop, we'll use **simple monotonically increasing version numbers** (`v1`, `v2`, `v3`, etc.). It's straightforward, easy to understand, and works well for most Fabric projects.

---

## Create a Tag in GitHub

Let's tag your current commit before deploying it to production.

1. Open [https://github.com](https://github.com)
2. Navigate to your repository (e.g., `fabric-devops-workshop`)
3. On the right side of your repository page, find the **Releases** section
4. Click on **Releases** (or **Create a new release** if you have none)
5. Click **Create a new release**
6. Click **Choose a tag**
7. Click **Create a new tag**
8. Type a new **tag name**: `v1` (or the next version number if you already have releases)
9. Click **Create new tag: v1 on publish**
10. For **Target**, make sure `main` (or your branch) is selected
11. Enter a **Release title**: `v1`
12. In the description, summarize what's included:
   ```
   Initial production release for Fabric DevOps Workshop
   
   - Hello Fabric notebook with basic PySpark examples
   ```
13. Click **Publish release**

> 💡 **Why Releases?** GitHub Releases are the most native way to manage release history—they give you a visible timeline, release notes, and an easy way to compare versions. The downside is that GitHub automatically creates source code archives (zip/tar.gz) with each release, which aren't necessary for Fabric workflows where code stays in Git and deploys via pipelines. If you'd prefer not to have the zips, you can use plain **Tags** instead (no release page, just a marker on the commit). For this workshop, we'll use Releases for their visibility and ease of use.

## Verify Your Tag

1. Go back to your repository's main page
2. Click on **Tags** (next to the branch dropdown, or in the Releases section)
3. You should see your tag (e.g., `v1`) listed

You now have a permanent marker for this version of your code!

---

## Tagging Conventions

We'll keep it simple: **use a monotonically increasing version number.**

Format: `v1`, `v2`, `v3`, etc.

Each time you deploy to production, increment the number:
- First release: `v1`
- Next release: `v2`
- And so on: `v3`, `v4`, `v5`...

This makes it easy to see your release history at a glance and communicate clearly ("we deployed v11" is much clearer than "we deployed commit a3f7b2c").

> 💡 **Note:** There are other tagging conventions out there—like semantic versioning (`v1.0.0`, `v1.1.0`) for products with formal release cycles, or date-based tags (`prod-2025-01-15`). For most Fabric projects, simple version numbers are straightforward and effective.

---

## The Workflow Going Forward

Now that you understand tagging, here's the recommended workflow for deploying to production:

```
┌─────────────────────────────────────────────────────────────────┐
│                    DEPLOYMENT WORKFLOW                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. Make changes      2. Commit to Git    3. Tag the commit     │
│     in Dev               (Lesson 1.2)        (This lesson)      │
│        │                      │                    │            │
│        ▼                      ▼                    ▼            │
│   ┌─────────┐          ┌───────────┐        ┌───────────┐       │
│   │   Dev   │    ───►  │   Git     │  ───►  │    v1     │       │
│   │Workspace│          │  Commit   │        │   Tag     │       │
│   └─────────┘          └───────────┘        └───────────┘       │
│                                                   │             │
│                                                   ▼             │
│  4. Deploy to Prod ◄──────────────────────────────┘             │
│     (Next lesson)                                               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

This way, you always know:
- What's in production (check the latest tag)
- When it was deployed (tag timestamp)
- What changed (compare tags in GitHub)

---

## Summary

In this lesson, you:

- ✅ Learned why tagging releases is important
- ✅ Created a tag/release in GitHub
- ✅ Understood different tagging conventions

### Key Concepts

1. **Tags** - Permanent markers for specific commits
2. **Releases** - Tags with descriptions and release notes
3. **Conventions** - Consistent naming makes history readable

Now you have your release tagged and ready to deploy!

---

**Previous:** [Lesson 2.1: Setting Up a Deployment Pipeline](lesson-2.1-setting-up-a-deployment-pipeline.md)  
**Next:** [Lesson 2.3: Deploying to Production](lesson-2.3-deploying-to-production.md)
