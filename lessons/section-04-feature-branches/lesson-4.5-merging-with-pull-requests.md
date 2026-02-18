# Lesson 4.5: Merging with Pull Requests

## Why This Lesson?

Your feature is complete and committed to a branch. Now you need to get it into `main`—but direct commits are blocked. The only way in is through a **pull request**.

Pull requests aren't just a merge mechanism—they're where code reviews happen, discussions take place, and changes get approved.

---

## Overview

In this lesson, you will:

- Create a pull request on GitHub
- Review and merge your changes
- Sync the Dev workspace with the merged changes

**Estimated Time:** 10 minutes

**Prerequisites:**
- Completed Lesson 4.4 (committed changes to a feature branch)

---

## Create a Pull Request

Your feature is complete. Time to merge it back to `main`.

> 💡 **Pull requests are a Git concept, not a Fabric feature.** Everything in this section happens in GitHub (or Azure DevOps), not in Fabric. PRs work the same way whether you're merging Fabric items, Python code, or any other files tracked in Git. This is the universal workflow for collaborating with Git.

1. Open [GitHub](https://github.com) in your browser and navigate to your repository
2. GitHub may show a banner: "feature-add-greeting had recent pushes" with a **Compare & pull request** button—click it
   
   Or manually: Click **Pull requests** > **New pull request** > set **base**: `main` and **compare**: `feature-add-greeting`

3. Add a title: `Add greeting message to notebook`
4. Click **Create pull request**

---

## Review and Merge

Now let's review the changes and merge.

1. Review the **Files changed** tab to see your changes
2. Click **Merge pull request**, then **Confirm merge**

> 💡 **This is where code reviews happen.** In a team environment, you'd configure branch policies to require approvals before merging. Teammates would review the **Files changed** tab, leave comments, and approve (or request changes). We skipped that setup for this workshop, but this is the step where that review process would occur.

> ✅ Your changes are now in `main`!

3. Click **Delete branch** (optional but recommended—the branch served its purpose)

---

## Sync the Dev Workspace

Your changes are in `main`, but the Dev workspace doesn't know yet.

1. Navigate back to your original **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Click **Source control**—you should see the workspace is behind the Git repo
3. Click **Update all** (or **Pull**) to sync the changes
4. Open the `01-hello-fabric` notebook and verify your greeting message is there

> ✅ The Dev workspace now has your merged changes.

---

## Summary

In this lesson, you:

- ✅ Created a pull request on GitHub
- ✅ Reviewed and merged your changes
- ✅ Synced the Dev workspace with the merged changes

### Key Takeaways

1. **Pull requests are the gateway** — All changes to `main` go through PRs
2. **PRs enable code review** — Teammates can review, comment, and approve
3. **Sync after merging** — Pull changes into your Dev workspace

---

**Previous:** [Lesson 4.4: Creating a Feature Branch](lesson-4.4-creating-a-feature-branch.md)  
**Next:** [Lesson 4.6: Cleaning Up](lesson-4.6-cleaning-up.md)
