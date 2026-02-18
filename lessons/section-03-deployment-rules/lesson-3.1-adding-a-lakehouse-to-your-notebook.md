# Lesson 3.1: Adding a Lakehouse to Your Notebook

## Why Deployment Rules?

So far, your notebook has been self-contained—it just prints messages and doesn't connect to any data. But real notebooks read from and write to data stores like **Lakehouses**.

Here's the problem: your Dev lakehouse and your Prod lakehouse are different. When you deploy your notebook from Dev to Prod, you don't want it still pointing at the Dev lakehouse. You need it to automatically switch to the Prod lakehouse.

**Deployment rules solve this:** You configure a rule that says "when deploying to Prod, use the Prod lakehouse instead."

Before we can set up that rule, we need a lakehouse. Let's create one and connect it to your notebook.

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Section 2 (Deployment Pipelines)
- Your `FabricDevOps-Workshop-Dev` workspace with the `01-hello-fabric` notebook

---

## Create a Lakehouse

A lakehouse is a data store in Fabric that combines the best of data lakes and data warehouses. For this workshop, we'll use it as a simple place to store data that our notebook can read and write.

1. Go to your **FabricDevOps-Workshop-Dev** workspace
2. Click **+ New item**
3. Select **Lakehouse** from the list
4. Name it `workshop_lakehouse`
5. Click **Create**

The lakehouse will open, showing an empty **Tables** and **Files** section. That's fine—we'll add data to it from our notebook.

---

## Set the Default Lakehouse for Your Notebook

Now let's connect your notebook to the lakehouse.

1. In your workspace, open the `01-hello-fabric` notebook
2. In the left panel of the notebook, look for the **Lakehouses** section
3. Click **Add** (or the **+ Add lakehouse** button)
4. Select **Existing lakehouse**
5. Choose `workshop_lakehouse` from the list
6. Click **Add**

You should now see `workshop_lakehouse` listed in the Lakehouses panel.

7. Hover over `workshop_lakehouse` in the Lakehouses panel
8. Click the **...** (more options) menu
9. Select **Set as default lakehouse**

> ✅ A checkmark or "default" indicator should appear next to the lakehouse name.

---

## Use the Lakehouse in Your Notebook

Let's add some code that writes to and reads from the lakehouse. This will prove our connection works.

1. Add a new code cell to your notebook with the following content:

```python
# Create a simple DataFrame
data = [
    ("Alice", 28),
    ("Bob", 35),
    ("Charlie", 42)
]
columns = ["Name", "Age"]

df = spark.createDataFrame(data, columns)

# Write to the default lakehouse
df.write.mode("overwrite").format("delta").saveAsTable("people")

print("✅ Data written to 'people' table in the default lakehouse!")
```

2. Click the **Run** button (▶) on the cell
3. Wait for execution to complete—you should see the success message
4. In the Lakehouses panel, click the **refresh** icon next to `workshop_lakehouse`
5. Expand the **Tables** section—you should see a `people` table

Now add another code cell to read the data back:

```python
# Read from the default lakehouse
df = spark.read.table("people")

# Display the data
display(df)

print(f"✅ Read {df.count()} rows from the default lakehouse!")
```

6. Run the cell
7. You should see the table data displayed and the success message

---

## Commit Your Changes

Now let's save these changes to Git.

1. Save the notebook (**Ctrl/Cmd + S**)
2. Open the **Source control** panel
3. You should see changes to:
   - The notebook (new code cells and lakehouse reference)
   - The new lakehouse
4. Enter a commit message:
   ```
   Add workshop lakehouse and connect to notebook
   ```
5. Click **Commit**

---

## Understanding the Problem

Here's what we have now:

```
┌─────────────────────────────────────────────────────────────────┐
│                   DEV WORKSPACE                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   01-hello-fabric notebook                                      │
│         │                                                       │
│         └──── default lakehouse ────→  workshop_lakehouse       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

If we deploy this notebook to Prod right now, what happens?

**The problem:** The notebook will still try to use `workshop_lakehouse` from the Dev workspace. But Prod should have its own lakehouse with its own data.

> 💡 **About Auto-Binding:** Here's something interesting—Fabric actually tries to help with this automatically. When items reference each other and they're all in the same workspace, Fabric uses **auto-binding** to fix the references during deployment. In this case, if you deploy the notebook and the lakehouse together, and then check the Prod copy of the notebook, you'll find that auto-bind already fixed it to point to the Prod lakehouse.
>
> **So why learn deployment rules?** Auto-binding only works when all the items are in the same workspace. It's very common to need references *outside* the workspace—like a shared lakehouse, a central data source, or a semantic model in another workspace. In those cases, auto-binding can't help and you need deployment rules. We'll practice creating deployment rules so you understand the concept for when you really need it.
>
> Auto-binding does a lot more than we cover here. For details, see the [auto-binding documentation](https://learn.microsoft.com/en-us/fabric/cicd/deployment-pipelines/understand-the-deployment-process#autobinding).

In the next lesson, we'll:
1. Create a lakehouse in the Prod workspace
2. Set up a **deployment rule** to swap the lakehouse when deploying

---

## Summary

In this lesson, you:

- ✅ Created a lakehouse in your Dev workspace
- ✅ Connected it to your notebook as the default lakehouse
- ✅ Added code to write and read data
- ✅ Committed the changes to Git

### What You Have Now

| Item | Location | Purpose |
|------|----------|---------|
| `01-hello-fabric` | Dev workspace | Notebook with lakehouse connection |
| `workshop_lakehouse` | Dev workspace | Data store for the notebook |

---

**Previous:** [Lesson 2.6: Adding a Test Environment](../section-02-deployment-pipelines/lesson-2.6-adding-a-test-environment.md)  
**Next:** [Lesson 3.2: Creating Deployment Rules](lesson-3.2-creating-deployment-rules.md)
