# Lesson 3.2: Creating Deployment Rules

## Why Deployment Rules?

In the previous lesson, we connected a lakehouse to our notebook. But here's the problem: when we deploy to Prod, we need the notebook to use a *different* lakehouse—one that exists in the Prod workspace.

Deployment rules tell the pipeline: "When you deploy this item to this stage, change this setting to this value."

---

## Overview

In this lesson, you will:

- Deploy the lakehouse to Production (via the pipeline)
- Configure a deployment rule to swap the default lakehouse
- Deploy again and verify the rule works

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lesson 3.1 (notebook connected to lakehouse in Dev)

---

## Deploy the Lakehouse to Production

Before we can create a deployment rule, the items must exist in the target stage. Let's deploy our changes to create the lakehouse in Prod.

1. Go to your **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Click **Source control** in the top menu
3. If there are uncommitted changes (lakehouse and/or notebook changes), commit them:
   - Add a commit message like `Add lakehouse and connect to notebook`
   - Click **Commit**

> 💡 **Remember:** If you have changes to deploy, tag them first! Create a tag like `v3` before deploying (see [Lesson 2.2](../section-02-deployment-pipelines/lesson-2.2-tagging-releases.md)).

4. In the left navigation, click **Workspaces**
5. At the bottom, click **Deployment pipelines**
6. Open your pipeline (`FabricDevOps-Workshop-Pipeline`)
7. Click **Deploy** from Development to Production
8. Review the items—you should see the lakehouse and notebook
9. Click **Deploy**
10. Wait for deployment to complete

> ✅ The lakehouse now exists in Prod! But there's a problem...

## Check the Lakehouse Binding

1. Go to your **Production** workspace
2. Open the `01-hello-fabric` notebook
3. Look at the **Lakehouses** panel on the left
4. Notice the default lakehouse is `workshop_lakehouse` from the **Prod** workspace

> ✅ **Auto-binding in action!** Fabric automatically connected the notebook to the Prod lakehouse because both items were deployed together to the same workspace. Pretty cool!

So why are we still going to create a deployment rule? Two reasons:

1. **Practice** — You need to know how to set up rules for when auto-binding *doesn't* cover your scenario
2. **Explicit is better** — Deployment rules give you explicit control and make your configuration visible to your team

---

## Configure the Deployment Rule

Now let's tell the pipeline to swap the lakehouse when deploying to Prod.

1. In the left navigation, click **Workspaces**
2. At the bottom, click **Deployment pipelines**
3. Open your pipeline (`FabricDevOps-Workshop-Pipeline`)
4. Look at the **Production** stage (the target stage where the rule applies)
5. Click **Deployment rules** (or the gear/settings icon for the stage)
6. You'll see a list of items that support deployment rules
7. Find your notebook (`01-hello-fabric`) in the list
8. Click on it to expand the rule options
9. Look for **Default lakehouse** setting
10. You should see a dropdown showing lakehouses in the target workspace
11. Select `workshop_lakehouse` from the Prod workspace
12. Click **Save**

> 💡 **No dropdown?** If you don't see a lakehouse picker, select **Other** and enter the Lakehouse ID you can find in the lakehouse's URL (the GUID after `/lakehouses/`).

> ✅ The rule is now configured. Every time you deploy to Prod, the notebook's default lakehouse will be set to the Prod lakehouse.

---

## Deploy Again and Verify

Let's deploy again to apply the rule.

1. In your pipeline, click **Deploy** from Development to Production
2. Even if there are no code changes, the rule will be applied
3. Click **Deploy**
4. Wait for the deployment to complete
5. Go to your **Production** workspace
6. Open the `01-hello-fabric` notebook
7. Look at the **Lakehouses** panel on the left
8. Confirm the default lakehouse is `workshop_lakehouse` from the **Prod** workspace (not Dev!)

> ✅ **Success!** The deployment rule swapped the lakehouse automatically.

### Test the Notebook (Optional)

1. Run the notebook in Production
2. It should write to and read from the **Prod** lakehouse
3. Check the Prod lakehouse—you should see the `people` table

---

## How Deployment Rules Work

Here's what happens during deployment:

```
┌─────────────────────────────────────────────────────────────────┐
│                    DEPLOYMENT WITH RULES                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   DEV WORKSPACE                      PROD WORKSPACE             │
│   ┌─────────────────┐                ┌─────────────────┐        │
│   │  01-hello-fabric│                │  01-hello-fabric│        │
│   │                 │    Deploy      │                 │        │
│   │  default LH:    │ ─────────────► │  default LH:    │        │
│   │  workshop-      │                │  workshop-      │        │
│   │  lakehouse(DEV) │    Rule        │  lakehouse(PROD)│        │
│   └─────────────────┘    Applied!    └─────────────────┘        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Without the rule:** The notebook would still reference the Dev lakehouse after deployment.

**With the rule:** The pipeline automatically swaps in the Prod lakehouse ID.

---

## When to Use Deployment Rules

Deployment rules are useful for any setting that differs between environments:

| Item Type | Common Rules |
|-----------|-------------|
| **Notebooks** | Default lakehouse, attached environment |
| **Semantic models** | Data source connections, parameters |
| **Dataflows** | Data source connections, parameters |
| **Paginated reports** | Data source connections |

> 💡 **Remember:** If items reference each other *within* the same workspace, auto-binding often handles it. Deployment rules are most valuable when you need to override auto-binding or reference items outside the workspace.

---

## Summary

In this lesson, you:

- ✅ Deployed the lakehouse to Production (items must exist before rules can reference them)
- ✅ Configured a deployment rule to swap the default lakehouse
- ✅ Deployed again and verified the rule worked

### Key Concepts

1. **Deployment rules** override item settings when deploying to a specific stage
2. **Rules are configured on the target stage** (where you're deploying *to*)
3. **Rules apply every deployment**—you set them once, and they work automatically

---

**Previous:** [Lesson 3.1: Adding a Lakehouse to Your Notebook](lesson-3.1-adding-a-lakehouse-to-your-notebook.md)  
**Next:** [Lesson 4.1: Inner Loop and Outer Loop](../section-04-feature-branches/lesson-4.1-inner-loop-outer-loop.md)
