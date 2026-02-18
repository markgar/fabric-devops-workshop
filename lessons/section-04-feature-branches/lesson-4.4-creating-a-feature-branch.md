# Lesson 4.4: Creating a Feature Branch

## Why This Lesson?

You've protected `main`, so you can't commit directly anymore. Now you need to create a feature branch—and a workspace connected to it—so you can actually get work done.

The good news? Fabric makes this easy with the **Branch out** feature.

---

## Overview

In this lesson, you will:

- Create a feature branch using Fabric's "Branch out" feature
- Get a new workspace connected to your branch
- Make changes and commit to your branch

**Estimated Time:** 10 minutes

**Prerequisites:**
- Completed Lesson 4.3 (branch protection configured)

---

## Create a Feature Branch

Let's create a branch to work on a new feature—we'll add a small enhancement to our notebook.

1. Go to your **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Click **Source control** in the top menu
3. Click **Branch out** (or look for the branch icon/dropdown)
4. Enter the following:
   - **Branch name**: `feature-add-greeting`
   - **Workspace name**: Fabric will suggest a name (you can shorten it)
5. Click **Branch out** to create the branch and workspace

> ✅ Fabric creates both the Git branch AND a new workspace connected to it—in one step!

Verify you're in your new workspace:
- Check the **Source control** panel—it should show you're on the `feature-add-greeting` branch
- Your workspace has copies of all the items from `main`

---

## Make Your Changes

Now let's make a change in our feature branch.

1. In your new workspace, open the `01-hello-fabric` notebook
2. Add a new cell at the top of your notebook with this code:

   ```python
   # Display a greeting
   print("Welcome to the Fabric DevOps Workshop!")
   print("=" * 40)
   ```

3. Run the new cell to make sure it works—you should see your greeting message

> 💡 **This is your inner loop!** You're working in isolation—nobody else is affected by your changes.

---

## Commit to Your Branch

Now let's save our work to Git.

1. Click **Source control** in the top menu
2. You should see your notebook has uncommitted changes
3. Enter a commit message: `Add greeting message to notebook`
4. Click **Commit**

> ✅ You've successfully committed to a feature branch. The `main` branch is unchanged. Next, we'll create a pull request to merge your work back to `main`.

---

## Summary

In this lesson, you:

- ✅ Created a feature branch using Fabric's **Branch out** feature
- ✅ Got a new workspace connected to your branch
- ✅ Made changes in your isolated workspace
- ✅ Committed to your feature branch

### Key Takeaways

1. **Branch out does the heavy lifting** — Creates branch + workspace in one step
2. **Work in isolation** — Your changes don't affect anyone until you merge

---

**Previous:** [Lesson 4.3: Configuring Branch Policies](lesson-4.3-configuring-branch-policies.md)  
**Next:** [Lesson 4.5: Merging with Pull Requests](lesson-4.5-merging-with-pull-requests.md)
