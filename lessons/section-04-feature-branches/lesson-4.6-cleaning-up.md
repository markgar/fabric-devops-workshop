# Lesson 4.6: Cleaning Up

## Why This Lesson?

Your feature is merged. The branch served its purpose. The workspace did too.

Now it's time to clean up—delete the branch, delete the workspace, and leave things tidy for the next feature.

---

## Overview

In this lesson, you will:

- Delete the feature branch on GitHub
- Delete the feature workspace in Fabric

**Estimated Time:** 5 minutes

**Prerequisites:**
- Completed Lesson 4.5 (merged your pull request)

---

## Delete the Feature Branch

If you didn't delete the branch when merging, do it now.

1. Go to your repository on [GitHub](https://github.com)
2. Click **Branches** (or find it under the Code tab)
3. Find `feature-add-greeting` in the list
4. Click the trash icon to delete it

> 💡 **Merged branches are safe to delete.** The commits are preserved in `main`. Deleting the branch just removes the pointer.

---

## Delete the Feature Workspace

Your feature workspace was temporary—you can delete it now.

1. Go to **Workspaces** in the Fabric left navigation
2. Find your feature workspace and click **...** → **Workspace settings**
3. Scroll down and click **Delete this workspace**
4. Confirm the deletion

> 💡 **Workspaces are cheap to create and delete.** Don't keep old feature workspaces around—they clutter your environment and can cause confusion.

---

## The Complete Feature Branch Flow

Here's the full workflow you've learned in Section 4:

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   1. BRANCH OUT           2. DEVELOP            3. MERGE            │
│   ┌─────────────────┐    ┌─────────────────┐   ┌─────────────────┐  │
│   │ Create branch   │    │ Work in your    │   │ Create PR       │  │
│   │ + workspace     │───►│ feature         │──►│ Merge to main   │  │
│   │ (Branch out)    │    │ workspace       │   │ (GitHub)        │  │
│   └─────────────────┘    └─────────────────┘   └─────────────────┘  │
│                                                                     │
│   4. SYNC                 5. CLEAN UP                               │
│   ┌─────────────────┐    ┌─────────────────┐                        │
│   │ Update Dev      │    │ Delete branch   │                        │
│   │ workspace       │    │ Delete workspace│                        │
│   └─────────────────┘    └─────────────────┘                        │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Summary

In this lesson, you:

- ✅ Deleted the feature branch on GitHub
- ✅ Deleted the feature workspace in Fabric

### Key Takeaways

1. **Delete merged branches** — They've served their purpose
2. **Delete feature workspaces** — Keep your environment clean
3. **This is a cycle** — You'll repeat this flow for every feature

---

## 🎉 Nice Work!

You've completed Section 4.

You now know how to:
- Connect Fabric workspaces to Git
- Make commits and undo changes
- Set up deployment pipelines with Dev → Test → Prod
- Tag releases and deploy through stages
- Configure deployment rules for environment-specific settings
- Use feature branches for isolated development
- Create pull requests and merge changes safely

Next, we’ll build on that foundation by introducing **variable libraries** so we can manage environment-specific configuration without hard-coding values.

---

**Previous:** [Lesson 4.5: Merging with Pull Requests](lesson-4.5-merging-with-pull-requests.md)  
**Next:** [Lesson 5.1: What Are Variable Libraries?](../section-05-variable-libraries/lesson-5.1-what-are-variable-libraries.md)
