# Lesson 1.2: Making Your First Commit

## Why Commits Matter

A commit is a snapshot of your work at a specific point in time. Think of it like a save point in a video game—you can always come back to it.

Without a Git-connected workspace, your changes exist only in Fabric. If something goes wrong, you have no way to recover. With commits, every meaningful change is recorded, described, and recoverable.

---

## Overview

Now that your workspace is connected to Git, it's time to create something and commit it. In this lesson, you will:

- Create a notebook in your Fabric workspace
- Commit it to your Git repository
- Make changes and commit again
- Learn how to write good commit messages
- View your commit history in GitHub

**Estimated Time:** 20-25 minutes

**Prerequisites:**
- Completed Lesson 1.1 (workspace connected to Git)

---

## Create a Notebook

Let's create your first notebook that we'll track with Git.

1. In your workspace, click **+ New item**
2. Select **Notebook** from the list of item types

   > 💡 If the list seems overwhelming, use the search box in the top right to filter it down.

3. Name your notebook `01-hello-fabric`
4. A new notebook will open in the editor
5. In the first cell, add a markdown cell by clicking the **M↓** button or selecting **Markdown** from the cell type dropdown
6. Add the following content:

```markdown
# My First Fabric Notebook

This notebook is part of the Fabric DevOps Workshop.

## Purpose
Learning how to use source control with Microsoft Fabric.
```

7. Click **+ Code** to add a new code cell
8. Add the following PySpark code:

```python
# Simple PySpark example
print("Hello from Fabric!")

# Display current date
from datetime import datetime
print(f"Notebook run at: {datetime.now()}")
```

> 💡 You don't need to worry about saving—Fabric saves automatically.

---

## Commit Your Changes

Now that you've created a notebook, let's commit it to your Git repository.

1. Navigate back to your workspace
2. Look for the **Source control** button in the workspace toolbar (it may show a number indicating uncommitted changes)
3. Click on it to open the source control panel
4. In the source control panel, you should see:
   - Your new notebook listed as a new/added item
   - A visual indicator showing it's a new file (a green circle with a white plus)
5. Select the **Changes** tab in the Source control panel
6. Check the box next to the items you want to commit (or check the top box to select all)
7. In the **Commit message** field, enter a descriptive message:
   ```
   Add initial hello-fabric notebook
   
   - Created first notebook for workshop
   - Added markdown documentation
   - Added simple PySpark print example
   ```
8. Click the **Commit** button

> ✅ **Success:** Your notebook is now saved in your Git repository!

---

## Make Changes and Commit Again

Let's modify the notebook to understand how Fabric tracks changes.

1. Open your `01-hello-fabric` notebook
2. Add a new code cell with the following content:

```python
# New feature: Calculate something
numbers = [1, 2, 3, 4, 5]
total = sum(numbers)
print(f"The sum of {numbers} is {total}")
```

Notice the following changes in your workspace:

1. **In the workspace item list** - You'll see a "not equal" sign (≠) next to the notebook, showing it has uncommitted changes
2. **In the source control panel** - The notebook also appears with a "not equal" sign (≠)

> 🔍 **Why This Matters:** These visual indicators help you quickly identify which items have been changed but not yet committed. This is crucial when working in teams to track what's been modified.

Now commit the changes:

1. Open the **Source control** panel
2. Select the modified notebook
3. Enter a meaningful commit message:
   ```
   Add sum calculation feature to hello-fabric notebook
   
   - Added new code cell demonstrating list operations
   - Shows sum calculation with formatted output
   ```
4. Click **Commit**

---

## Understanding Commit Messages

### Why Are Commit Messages Important?

Good commit messages are essential for:

| Reason | Explanation |
|--------|-------------|
| **History Tracking** | They create a log of what changed and why |
| **Collaboration** | Team members can understand changes without reading all the code |
| **Debugging** | When something breaks, you can trace back to find which change caused it |
| **Code Reviews** | Reviewers can quickly understand the purpose of changes |
| **Rollbacks** | If you need to undo changes, good messages help identify what to revert |

### Best Practices for Commit Messages

1. **Be Specific:** "Add sum calculation feature" is better than "Updated notebook"
2. **Use Present Tense:** "Add feature" not "Added feature"
3. **Keep the First Line Short:** Aim for 50 characters or less
4. **Add Details if Needed:** Use additional lines to explain the "why" behind changes
5. **Reference Issues:** If using issue tracking, reference ticket numbers

#### Examples of Good vs. Bad Commit Messages

❌ **Bad:**
- "fix"
- "updates"
- "changed stuff"
- "WIP"

✅ **Good:**
- "Fix null pointer exception in data transformation"
- "Add customer segmentation logic to analytics notebook"
- "Update connection string for production lakehouse"

---

## View History in GitHub

Now let's see how your commits appear in GitHub.

1. Open [https://github.com](https://github.com) in a new browser tab
2. Navigate to your repository (e.g., `fabric-devops-workshop`)
3. Click on the **commits** link (usually shows the number of commits, or click on the clock icon with the commit count)
4. You'll see a list of all commits with:
   - The commit message
   - The author
   - The timestamp
   - A unique commit hash (SHA)

### Explore a Specific Commit

1. Click on any commit message to view the details
2. You'll see:
   - **Files changed** - Which files were modified
   - **Diff view** - Line-by-line changes (green for additions, red for deletions)
   - **Full commit message** - Including any additional details

### View File History

1. Navigate to your notebook file in the repository (it will be in a folder structure like: `01-hello-fabric/notebook-content.py` or similar)
2. Click on the file
3. Click the **History** button (clock icon) to see all commits that modified this file
4. You can click on any historical version to see what the file looked like at that point

> 🎯 **Key Insight:** This is the power of version control! You can always go back to any previous version of your work. If you make a mistake or need to reference old code, it's all preserved in the history.

---

## Summary

In this lesson, you:

- ✅ Created a notebook and committed it to source control
- ✅ Modified the notebook and observed change tracking indicators
- ✅ Wrote meaningful commit messages
- ✅ Explored commit history in GitHub

### Key Concepts

1. **Commits** - Snapshots of your work at a point in time
2. **Change Tracking** - Visual indicators show which items have uncommitted changes
3. **Commit Messages** - Descriptive messages are crucial for maintaining a useful history
4. **Version History** - Git preserves every version, allowing you to review previous states

---

## Troubleshooting

### Common Issues

**Issue: Changes not showing in source control**
- Make sure you've saved your notebook (Ctrl/Cmd + S)
- Refresh the workspace
- Check that the workspace is still connected to Git

**Issue: Commit fails**
- Check your network connection
- Ensure you have write permissions to the repository
- Verify the branch isn't protected

---

**Previous:** [Lesson 1.1: Connecting Your Workspace to Git](lesson-1.1-connecting-your-workspace-to-git.md)  
**Next:** [Lesson 1.3: Undoing Uncommitted Changes](lesson-1.3-undoing-uncommitted-changes.md)
