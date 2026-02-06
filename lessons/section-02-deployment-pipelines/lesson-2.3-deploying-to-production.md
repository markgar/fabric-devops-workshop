# Lesson 2.3: Deploying to Production

## Why Use a Pipeline to Deploy?

You could just copy items manually between workspaces. But a deployment pipeline gives you:

- **A record** of what was deployed and when
- **Comparison tools** to see differences between environments
- **Consistency** in how deployments happen every time

This matters when something breaks and you need to know exactly what changed.

---

## Overview

You've set up your deployment pipeline and tagged your release. Now it's time to deploy your content from Development to Production.

In this lesson, you will:

- Deploy content from your dev workspace to prod
- Understand what gets deployed
- Verify the deployment in your production workspace

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lesson 2.1 (deployment pipeline set up)
- Completed Lesson 2.2 (release tagged in Git)

---

## Open Your Deployment Pipeline

1. In the left navigation pane, click on **Workspaces**
2. At the bottom of the workspaces panel, click on **Deployment pipelines**
3. Click on your pipeline (e.g., `FabricDevOps-Workshop-Pipeline`)

Before deploying, take a look at your pipeline:

- **Development stage:** Shows your notebook and any other items
- **Production stage:** Should be empty (nothing deployed yet)

You'll also see a **comparison indicator** between the stages showing that they're different.

---

## Deploy to Production

Fabric's deployment pipeline UI works from the perspective of the **target stage**—the stage you're deploying *to*.

1. Click on the **Production** stage card to select it
2. The bottom pane shows a comparison between Production and the source stage
3. Next to the **Deploy** button, confirm the dropdown shows **Development** as the source
4. Select the items you want to deploy
5. Click **Deploy** (the button shows the number of items that will be deployed)
6. A confirmation dialog appears—optionally add a deployment note (recommended for tracking)
7. Click **Deploy** to confirm
8. Wait for the deployment to complete

> ⏳ **Deployment may take a minute or two** depending on the number of items.

You'll see a progress indicator, and then a success message when it's done.

After deployment completes, you should see your item now appears in the Production stage and the comparison shows **Same as source**.

---

## Verify the Deployment

After deployment, look at your pipeline:

- **Development** and **Production** should now show the same items
- The comparison indicator should show they're **in sync** (identical)

1. Click on the **Production** stage in the pipeline (or navigate to your production workspace directly: `FabricDevOps-Workshop-Prod`)
2. You should see:
   - Your `01-hello-fabric` notebook
   - Any other items you had in development
3. Open the notebook in the production workspace
4. Confirm the content matches what you had in development

🎉 **Congratulations!** You've deployed to production!

---

## Understanding What Happened

### What Got Deployed?

When you deploy, Fabric copies the **item definitions** from one stage to another:

| What's Copied | What's NOT Copied |
|---------------|-------------------|
| Notebook code and structure | Data in lakehouses |
| Report definitions | Refreshed dataset data |
| Pipeline definitions | Scheduled refresh history |
| Semantic model structure | User permissions (by default) |

> 💡 **Key Point:** Deployment copies the **definitions**, not the data. If you have a lakehouse with data, the data stays in each environment separately.

### The Deployment Record

Fabric keeps a record of each deployment:

1. In your pipeline, click on the **History** icon (clock icon)
2. You'll see a log of all deployments with:
   - Who deployed
   - When they deployed
   - What was deployed

This history, combined with your Git tags, gives you a complete audit trail.

---

## The Complete Workflow

You've now completed the full dev-to-prod workflow:

```
┌─────────────────────────────────────────────────────────────────┐
│                 COMPLETE DEPLOYMENT WORKFLOW                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. Build in Dev    2. Commit & Tag    3. Deploy to Prod        │
│                                                                 │
│   ┌─────────┐       ┌───────────┐       ┌─────────────┐         │
│   │   Dev   │ ───►  │    Git    │ ───►  │    Prod     │         │
│   │Workspace│       │    v1     │       │  Workspace  │         │
│   └─────────┘       └───────────┘       └─────────────┘         │
│                                                                 │
│   ✓ Make changes    ✓ Permanent        ✓ Users see              │
│   ✓ Test locally      record             stable content         │
│                     ✓ Can rollback                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Summary

In this lesson, you:

- ✅ Deployed content from Development to Production
- ✅ Verified the deployment in your production workspace
- ✅ Learned what gets deployed (definitions, not data)
- ✅ Saw the deployment history

### Key Concepts

1. **Deploy** - Copy item definitions from one stage to another
2. **Comparison** - Pipeline shows differences between stages
3. **History** - All deployments are recorded for audit purposes

---

## What's Next?

You now have a working dev/prod setup! In real projects, you might also want to:

- Configure **deployment rules** to handle environment-specific settings
- Add a **Test** stage for additional validation
- Set up **permissions** differently per environment

---

**Previous:** [Lesson 2.2: Tagging Releases](lesson-2.2-tagging-releases.md)  
**Next:** [Lesson 2.4: Viewing Previous Releases with Tags](lesson-2.4-viewing-previous-releases.md)
