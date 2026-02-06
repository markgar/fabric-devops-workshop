# Lesson 1.1: Connecting Your Workspace to Git

## Why Source Control? Problems Git Solves

Before we dive in, let's talk about **why** source control matters. If you've been developing notebooks, reports, or data pipelines, you've probably experienced some of these painful scenarios:

### 🤦 "I broke it and can't get it back"

You make changes to a working notebook, and suddenly nothing works. You try to undo, but you've already saved over the working version. Without source control, that working version is gone forever.

**Git solves this:** Every commit is a snapshot you can return to. Break something? Roll back to the last working version in seconds.

### 📁 "Which version is the correct one?"

Your folder looks like this:
```
sales_report.pbix
sales_report_v2.pbix
sales_report_FINAL.pbix
sales_report_FINAL_v2.pbix
sales_report_FINAL_v2_fixed.pbix
sales_report_FINAL_v2_fixed_USE_THIS_ONE.pbix
```

Sound familiar?

**Git solves this:** One file, complete history. Every version is preserved in the commit history with a clear message explaining what changed and why.

###  "Who changed this, and why?"

Something that used to work is now broken. You need to find out what changed, when it changed, and who changed it—but nobody remembers.

**Git solves this:** Complete audit trail. Every change is attributed to a person, timestamped, and (if you write good commit messages) explained. You can also produce release notes really easily by querying the commit messages.

---

### The Bottom Line

| Without Source Control | With Source Control |
|------------------------|---------------------|
| Hope you don't make mistakes | Mistakes are reversible |
| Guess which version is current | Clear history and single source of truth |
| Wonder what changed and when | Complete audit trail with attribution |

**Source control isn't just for software developers.** It's for anyone who creates things that change over time and matter to the business. That includes your Fabric notebooks, pipelines, semantic models, and all other Fabric items.

Now let's get started!

---

## Overview

In this lesson, you will set up your Fabric workspace and connect it to a Git repository. By the end of this lesson, you will have:

- A Microsoft Fabric workspace
- A Git repository (GitHub or Azure DevOps)
- Your workspace connected to Git and ready for version control

**Estimated Time:** 15-20 minutes

**Prerequisites:**
- A Microsoft Fabric capacity (trial or paid)
- A GitHub account OR an Azure DevOps organization
- For GitHub: A [personal access token](https://github.com/settings/tokens) with **repo** scope (classic) or **Contents** read/write permission (fine-grained)

> ⚠️ **Admin Note:** Your Fabric tenant admin must enable "Users can synchronize workspace items with their Git repositories" in the admin portal. If you can't see the Git integration option, contact your admin.

---

## Create a Fabric Workspace

A workspace is a collaborative environment in Microsoft Fabric where you create and manage your data items like notebooks, lakehouses, and pipelines.

1. Open your browser and go to [https://app.fabric.microsoft.com](https://app.fabric.microsoft.com)
2. Sign in with your Microsoft account
3. In the left navigation pane, click on **Workspaces**
4. Click the **+ New workspace** button
5. Enter a name for your workspace (e.g., `FabricDevOps-Workshop`)
6. Expand the **Advanced** section
7. Ensure you have a Fabric capacity selected under **License mode**
8. Click **Apply**

> 💡 **Tip:** Choose a descriptive name for your workspace that indicates its purpose. This makes it easier to identify later.

Your new workspace is now created and you should be taken to it automatically.

---

## Create a Git Repository

Before connecting Fabric to Git, you need a repository to connect to.

### Option A: Using GitHub

1. Go to [https://github.com](https://github.com) and sign in
2. Click the **+** icon in the top right corner
3. Select **New repository**
4. Enter a repository name (e.g., `fabric-devops-workshop`)
5. Choose **Private** or **Public** based on your preference
6. Check **Add a README file**
7. Click **Create repository**

### Option B: Using Azure DevOps

1. Go to [https://dev.azure.com](https://dev.azure.com) and sign in
2. Create a new project or use an existing one
3. Navigate to **Repos** in your project
4. Note your repository URL for later use

---

## Connect Your Workspace to Git

Now we'll connect your Fabric workspace to your Git repository. This enables version control for all the items you create.

1. In your Fabric workspace, click on the **Workspace settings** icon (gear icon) in the top right
2. In the left menu, select **Git integration**
3. Click **Connect** to begin the setup process

### For GitHub:

1. Select **GitHub** as your Git provider
2. Click **Add account** (if this is your first time connecting)
3. Enter a **Display name** (must be unique for each GitHub user)
4. Enter your **Personal access token** (the one you created in the prerequisites)
5. Optionally, enter a **Repository URL** to scope the connection to a specific repository
6. Click **Connect** to allow Fabric to access your GitHub account
7. Select the **Repository** you created earlier (or enter the URL)
8. Select the **Branch** (typically `main`)
   
   > 💡 **No branch showing?** If you don't see a branch, you probably didn't check "Add a README file" when creating the repo. The README creates the initial commit, which creates the `main` branch. Go back to GitHub and add a README to fix this.

9. Leave the **Git folder** as the default (don't put it in a subfolder for now)
10. Click **Connect and sync**

### For Azure DevOps:

1. Select **Azure DevOps** as your Git provider
2. Select your **Organization**
3. Select your **Project**
4. Select the **Repository**
5. Select the **Branch** (typically `main`)
6. Leave the **Git folder** as the default
7. Click **Connect and sync**

> ⏳ **Wait:** The initial sync may take a moment. You'll see a progress indicator.

## Verify the Connection

Once connected, you should see:
- A **Source control** panel appear in your workspace
- The branch name displayed in the workspace header
- A sync status indicator

🎉 **Congratulations!** Your workspace is now connected to Git!

---

## Summary

In this lesson, you:

- ✅ Created a new Microsoft Fabric workspace
- ✅ Created a Git repository (GitHub or Azure DevOps)
- ✅ Connected your workspace to the repository

Your workspace is now ready for version control. Any items you create can be committed to Git, tracked over time, and shared with your team.

---

## Troubleshooting

### Common Issues

**Issue: Can't see Git integration option**
- Your tenant admin needs to enable "Users can synchronize workspace items with their Git repositories"
- Contact your Fabric administrator

**Issue: Can't connect to GitHub**
- Ensure your personal access token has the correct permissions (repo scope or Contents read/write)
- Check that your repository exists and you have write access
- Try creating a new personal access token

**Issue: Connection fails for Azure DevOps**
- Verify you're signed into the correct Azure DevOps account
- Check that you have access to the organization, project, and repository
- Ensure the repository URL format is correct

---

**Next:** [Lesson 1.2: Making Your First Commit](lesson-1.2-making-your-first-commit.md)
