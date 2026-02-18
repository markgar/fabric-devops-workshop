# Lesson 5.2: Creating a Variable Library

## Why This Lesson?

A variable library only helps if it’s the single “source of truth” for environment-specific values.

In this lesson, we’ll create one library in Dev and define a `Prod` value set (in addition to the default values, which we’ll treat as Dev). Later, we’ll deploy it forward and make Production use the `Prod` set.

> 💡 **Docs note:** A variable library always has a **default value set**. When you first deploy or commit a variable library, the active value set starts as the default. In this workshop, we’ll treat the default values as our **Dev** values.

---

## Overview

In this lesson, you will:

- Create a variable library item
- Add variables we’ll use in a notebook
- Create a `Prod` value set
- Set values for Dev (default) and Prod

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lesson 5.1
- Your Dev workspace connected to `main`

---

## Create the Variable Library

1. Go to your **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Select **+ New item**
3. Search for and select **Variable library**
4. Name it `EnvConfig`
5. Select **Create**

> ✅ You should now see an `EnvConfig` item in your workspace.

---

## Add Variables

Let’s keep this simple and focused.

1. Open the `EnvConfig` variable library
2. Add these variables (these defaults are your **Dev** values):

| Name | Type | Example value |
|------|------|---------------|
| `RunLabel` | String | `dev` |
| `RowCount` | Integer | `10` |
| `TableName` | String | `workshop_seed_dev` |

> 💡 Use names that are obvious and boring. These variables should feel like configuration, not code.

---

## Create Value Sets and Set Values

Now create one alternative value set:

1. Create a value set named `Prod`

Then set values like (Dev comes from the default values you already entered):

| Variable | Dev (default) | Prod |
|---------|--------------|------|
| `RunLabel` | `dev` | `prod` |
| `RowCount` | `10` | `100` |
| `TableName` | `workshop_seed_dev` | `workshop_seed_prod` |

> ⚠️ Keep `RowCount` small in this workshop so runs finish quickly.

> 💡 Optional: If you decide to add a Test stage later (see Section 2), you can also create a `Test` value set and fill in values like `RunLabel=test`, `RowCount=25`, `TableName=workshop_seed_test`.

---

## Save and Commit

We want this to flow forward by automation (deployments and/or Git sync), not hand edits in Prod.

1. Select **Save** in the variable library
2. Open **Source control**
3. Confirm the variable library shows as changed
4. Commit with a message like:
   ```
   Add EnvConfig variable library
   ```

---

## Summary

In this lesson, you:

- ✅ Created a variable library (`EnvConfig`)
- ✅ Added three variables we’ll consume from a notebook
- ✅ Created Dev/Prod value sets and set values
- ✅ Committed the library to Git

---

**Previous:** [Lesson 5.1: What Are Variable Libraries?](lesson-5.1-what-are-variable-libraries.md)  
**Next:** [Lesson 5.3: Using Library Variables in a Notebook](lesson-5.3-using-library-variables-in-a-notebook.md)
