# Fabric DevOps Workshop

A hands-on workshop for learning source control and DevOps practices with Microsoft Fabric.

> 💡 **GitHub or Azure DevOps?** This workshop uses GitHub for examples, but the process works almost exactly the same with Azure DevOps. Both platforms use Git, so the core concepts—commits, branches, pull requests—are identical.

## Prerequisites

These prerequisites are essential — the workshop is hands-on from start to finish, and you won't be able to follow along without them. Please verify everything below is in place **before** the workshop begins.

- Each attendee needs the ability to create workspaces, OR have 2 workspaces pre-created for them with that attendee added as an admin on both workspaces. Workspaces must be attached to a Premium capacity or a Fabric capacity.
- A GitHub account OR an Azure DevOps organization
- For GitHub: A [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) with **repo** scope (classic) or **Contents** read/write permission (fine-grained)
- For GitHub: Admin access to your repository (needed to configure branch protection rules in Section 4)

> ⚠️ **Admin Note:** Your Fabric tenant admin must enable the following settings in the admin portal:
> - "Users can create Fabric items" — we use Fabric items during this workshop to keep things simple, so this needs to be enabled.
> - "Users can synchronize workspace items with their Git repositories" — if you can't see the Git integration option, contact your admin.

---

## Workshop Outline

> 💡 **Lectures:** Some sections begin with a lecture slide deck (lesson X.0) that introduces key concepts before the hands-on exercises. These are [Marp](https://marp.app/) presentations—open the markdown file and use the Marp extension to preview or export slides.

### Section 1: Git Basics

| Lesson | Title | Duration |
|--------|-------|----------|
| 1.0 | [Lecture](https://markgar.github.io/fabric-devops-workshop/marp-source/section-01.html) | 15 min |
| 1.1 | [Connecting Your Workspace to Git](lessons/section-01-git-basics/lesson-1.1-connecting-your-workspace-to-git.md) | 15-20 min |
| 1.2 | [Making Your First Commit](lessons/section-01-git-basics/lesson-1.2-making-your-first-commit.md) | 20-25 min |
| 1.3 | [Undoing Uncommitted Changes](lessons/section-01-git-basics/lesson-1.3-undoing-uncommitted-changes.md) | 5-10 min |

### Section 2: Deployment Pipelines

| Lesson | Title | Duration |
|--------|-------|----------|
| 2.0 | [Lecture](https://markgar.github.io/fabric-devops-workshop/marp-source/section-02.html) | 15 min |
| 2.1 | [Setting Up a Deployment Pipeline](lessons/section-02-deployment-pipelines/lesson-2.1-setting-up-a-deployment-pipeline.md) | 15-20 min |
| 2.2 | [Tagging Releases](lessons/section-02-deployment-pipelines/lesson-2.2-tagging-releases.md) | 10-15 min |
| 2.3 | [Deploying to Production](lessons/section-02-deployment-pipelines/lesson-2.3-deploying-to-production.md) | 10-15 min |
| 2.4 | [Viewing Previous Releases with Tags](lessons/section-02-deployment-pipelines/lesson-2.4-viewing-previous-releases.md) | 10 min |
| 2.5 | [Practice - Tag and Deploy Again](lessons/section-02-deployment-pipelines/lesson-2.5-practice-tag-and-deploy.md) | 5-10 min |
| 2.6 | [Adding a Test Environment](lessons/section-02-deployment-pipelines/lesson-2.6-adding-a-test-environment.md) | 5 min |

### Section 3: Deployment Rules

| Lesson | Title | Duration |
|--------|-------|----------|
| 3.0 | [Lecture](https://markgar.github.io/fabric-devops-workshop/marp-source/section-03.html) | 10 min |
| 3.1 | [Adding a Lakehouse to Your Notebook](lessons/section-03-deployment-rules/lesson-3.1-adding-a-lakehouse-to-your-notebook.md) | 10-15 min |
| 3.2 | [Creating Deployment Rules](lessons/section-03-deployment-rules/lesson-3.2-creating-deployment-rules.md) | 10-15 min |

### Section 4: Feature Branches

| Lesson | Title | Duration |
|--------|-------|---------|
| 4.0 | [Lecture](https://markgar.github.io/fabric-devops-workshop/marp-source/section-04.html) | 10 min |
| 4.1 | [Inner Loop and Outer Loop](lessons/section-04-feature-branches/lesson-4.1-inner-loop-outer-loop.md) | 5 min |
| 4.2 | [Branching Strategy](lessons/section-04-feature-branches/lesson-4.2-branching-strategy.md) | 10 min |
| 4.3 | [Configuring Branch Policies](lessons/section-04-feature-branches/lesson-4.3-configuring-branch-policies.md) | 10 min |
| 4.4 | [Creating a Feature Branch](lessons/section-04-feature-branches/lesson-4.4-creating-a-feature-branch.md) | 10-15 min |
| 4.5 | [Merging with Pull Requests](lessons/section-04-feature-branches/lesson-4.5-merging-with-pull-requests.md) | 10 min |
| 4.6 | [Cleaning Up](lessons/section-04-feature-branches/lesson-4.6-cleaning-up.md) | 5 min |

### Section 5: Variable Libraries

| Lesson | Title | Duration |
|--------|-------|---------|
| 5.0 | [Lecture](https://markgar.github.io/fabric-devops-workshop/marp-source/section-05.html) | 10 min |
| 5.1 | [What Are Variable Libraries?](lessons/section-05-variable-libraries/lesson-5.1-what-are-variable-libraries.md) | 5-10 min |
| 5.2 | [Creating a Variable Library](lessons/section-05-variable-libraries/lesson-5.2-creating-a-variable-library.md) | 10-15 min |
| 5.3 | [Using Library Variables in a Notebook](lessons/section-05-variable-libraries/lesson-5.3-using-library-variables-in-a-notebook.md) | 10-15 min |
| 5.4 | [Deploying and Selecting Active Value Sets](lessons/section-05-variable-libraries/lesson-5.4-deploying-and-selecting-active-value-sets.md) | 10-15 min |
| 5.5 | [Other Ways to Use Variable Libraries](lessons/section-05-variable-libraries/lesson-5.5-other-ways-to-use-variable-libraries.md) | 10 min |

---

## Future Topics

- Deployment Pipeline Parameters
- Handling Merge Conflicts
- Automated Testing in Pull Requests
- CI/CD with GitHub Actions or Azure DevOps Pipelines (ISV scenarios)

---

## License

This project is licensed under the [MIT License](LICENSE).