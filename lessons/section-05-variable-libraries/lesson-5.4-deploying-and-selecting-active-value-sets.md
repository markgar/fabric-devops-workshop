# Lesson 5.4: Deploying and Selecting Active Value Sets

## Why This Lesson?

You said you don’t want to modify Prod by hand—which is the right instinct.

That means:

- We edit the variable library in Dev
- We deploy changes forward through the deployment pipeline
- We configure each stage to use the correct **active value set**

Once that’s done, updates flow forward by automation.

---

## Overview

In this lesson, you will:

- Deploy the variable library and notebook to Prod
- Set the active value set in Prod to `Prod`
- Run the notebook in Prod and verify the behavior changed

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lessons 5.1–5.3
- A deployment pipeline with Dev → Prod configured

---

## Deploy the Changes Forward

1. Open your deployment pipeline
2. Make sure the following items are included in the deployment:
   - `EnvConfig` variable library
   - Your updated notebook (`01-hello-fabric`)
3. Deploy from **Dev → Prod**

> ✅ After deployment, the variable library item should exist in each stage’s workspace.

---

## Set the Active Value Set Per Stage

Now we tell each stage which value set to use.

1. In the **Prod** stage workspace:
   - Open `EnvConfig`
   - Set the active value set to `Prod`
   - Save

> 💡 The active value set is stage configuration. Deployments generally don’t overwrite which set is selected.

> 💡 **Compare tip:** Changing which value set is active typically does *not* show up as “different from source” in deployment pipeline comparisons. But adding/removing variables or value sets (or renaming/reordering them) will.

---

## Run and Verify in Each Stage

1. In the **Prod** stage workspace:
   - Open the notebook
   - Run the cell that generates/writes data
   - Verify the output shows `RunLabel = prod` and writes to the `workshop_seed_prod` table

> ✅ Same notebook code, different behavior—driven by the stage’s active value set.

---

## What Changes Going Forward?

From here on out, treat the variable library like any other artifact:

- Update values in Dev (and commit)
- Deploy forward
- Don’t hand-edit Prod

> ⚠️ If someone hand-edits variables or value sets in Prod, your deployment pipeline comparisons may show the library as “different from source.” That’s a signal you’ve drifted.

> 💡 Optional (if you add a Test stage later): Create a `Test` value set and select it as the active set in Test. This workshop’s core exercises use Dev → Prod only.

---

## Summary

In this lesson, you:

- ✅ Deployed the variable library + notebook through Dev → Prod
- ✅ Set `Prod` as the active set in Production
- ✅ Verified environment-specific behavior without changing code

---

**Previous:** [Lesson 5.3: Using Library Variables in a Notebook](lesson-5.3-using-library-variables-in-a-notebook.md)  
**Next:** [Lesson 5.5: Other Ways to Use Variable Libraries](lesson-5.5-other-ways-to-use-variable-libraries.md)
