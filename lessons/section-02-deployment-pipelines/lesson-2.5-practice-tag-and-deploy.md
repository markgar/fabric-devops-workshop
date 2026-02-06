# Lesson 2.5: Practice - Tag and Deploy Again

## Overview

Let's practice the complete deployment workflow one more time. You made a new change in the previous lesson—now let's deploy it to production.

This reinforces the workflow you'll use every time you deploy:

1. Tag the release
2. Deploy to production

**Estimated Time:** 5-10 minutes

**Prerequisites:**
- Completed Lesson 2.4 (new change committed)

---

## Tag the New Release

1. Open [https://github.com](https://github.com)
2. Navigate to your repository
3. Click on **Releases** (on the right side)
4. Click **Draft a new release**
5. Click **Choose a tag**
6. Click **Create a new tag**
7. Enter a new tag: `v2`
8. Click **Create new tag: v2 on publish**
9. Enter a **Release title**: `v2`
10. In the description, note what's new:
   ```
   Added new feature to hello-fabric notebook
   ```
11. Click **Publish release**

## Verify Your Tags

1. Go to **Tags** in your repository
2. You should now see two tags:
   - `v1` (first deployment)
   - `v2` (this deployment)

---

## Deploy to Production

1. In Fabric, navigate to **Deployment pipelines**
2. Open your pipeline
3. Before deploying, notice:
   - The **Development** and **Production** stages show they're **different**
   - Development has the new feature; Production doesn't
4. Click on the **Production** stage to select it
5. Confirm the dropdown next to **Deploy** shows **Development** as the source
6. Select the items you want to deploy
7. Click **Deploy** (the button shows the number of items)
8. Optionally add a deployment note
9. Click **Deploy** to confirm
10. Wait for completion

## Verify

1. Check that the stages now show as **in sync**
2. Optionally, open the production workspace and verify the notebook has the new feature

---

## Review Your Release History

You now have a deployment history in two places:

### In GitHub (Tags)

1. Go to your repository's **Releases** or **Tags**
2. You see both releases with descriptions of what changed
3. Click on either tag to see the code at that point in time

### In Fabric (Deployment History)

1. In your deployment pipeline, click the **History** icon
2. You see a log of both deployments with timestamps

---

## The Workflow You've Learned

```
┌─────────────────────────────────────────────────────────────┐
│              DEPLOYMENT WORKFLOW (Every Time)               │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   1. Make changes in Dev                                    │
│              │                                              │
│              ▼                                              │
│   2. Commit to Git                                          │
│              │                                              │
│              ▼                                              │
│   3. When ready to deploy: TAG it (v1, v2, v3, etc.)        │
│              │                                              │
│              ▼                                              │
│   4. Deploy via pipeline                                    │
│              │                                              │
│              ▼                                              │
│   5. Verify in production                                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Summary

In this lesson, you:

- ✅ Tagged a second release
- ✅ Deployed to production again
- ✅ Verified you have a history of both deployments

### You Now Have

- Two tagged releases in GitHub
- Two deployments in your pipeline history
- Production that matches your latest tag
- A repeatable process for future deployments

---

**Previous:** [Lesson 2.4: Viewing Previous Releases with Tags](lesson-2.4-viewing-previous-releases.md)  
**Next:** [Lesson 2.6: Adding a Test Environment](lesson-2.6-adding-a-test-environment.md)
