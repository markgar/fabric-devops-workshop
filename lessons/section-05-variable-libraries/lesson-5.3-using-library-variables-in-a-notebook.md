# Lesson 5.3: Using Library Variables in a Notebook

## Why This Lesson?

A variable library is only useful if other items actually consume it.

In this lesson, we’ll update a notebook to read values from the variable library and then use those values to control what the notebook does.

We’ll keep it self-contained by generating data inside the notebook—no external sources required.

---

## Overview

In this lesson, you will:

- Add library variables to a Fabric notebook
- Use those variables to generate and write data
- Commit the notebook changes to Git

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lesson 5.2
- Completed Lesson 3.1 (you have a default lakehouse connected to your notebook)

---

## Open Your Notebook

1. Go to your **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Open the `01-hello-fabric` notebook

---

## Add Library Variables to the Notebook

In Fabric notebooks, the docs-backed way to read variable library values is through **NotebookUtils**.

> ⚠️ **Important limitation:** `notebookutils.variableLibrary` only supports accessing variable libraries within the **same workspace**. That’s perfect for this workshop, because each stage has its own workspace copy after deployment.

1. Add a new cell near the top of the notebook
2. Paste the following code and run it:

```python
from pyspark.sql.functions import lit, current_timestamp

# Read values from the active value set of the EnvConfig variable library
run_label = notebookutils.variableLibrary.get("$(/**/EnvConfig/RunLabel)")
row_count = int(notebookutils.variableLibrary.get("$(/**/EnvConfig/RowCount)"))
table_name = notebookutils.variableLibrary.get("$(/**/EnvConfig/TableName)")

print(f"RunLabel = {run_label}")
print(f"RowCount = {row_count}")
print(f"TableName = {table_name}")

# Generate self-contained data (no external sources)
df = (
   spark.range(row_count)
      .withColumnRenamed("id", "row_id")
      .withColumn("run_label", lit(run_label))
      .withColumn("created_utc", current_timestamp())
)

# Write to the default lakehouse
df.write.mode("overwrite").format("delta").saveAsTable(table_name)

print(f"✅ Wrote {row_count} rows to '{table_name}'")
```

> 💡 The notebook resolves values from the **active** value set of `EnvConfig` in the current workspace.

---

## Verify the Result

1. In the notebook’s Lakehouses panel, refresh the lakehouse
2. Expand **Tables**
3. Confirm you see the table name from `TableName` (for example `workshop_seed_dev`)
4. Optionally preview the data and confirm it includes the run label

---

## Commit Your Changes

1. Open **Source control**
2. Commit with a message like:
   ```
   Use EnvConfig variables in notebook
   ```

---

## Summary

In this lesson, you:

- ✅ Connected the notebook to `EnvConfig` library variables
- ✅ Used variable values to control output and table naming
- ✅ Committed the notebook changes

---

**Previous:** [Lesson 5.2: Creating a Variable Library](lesson-5.2-creating-a-variable-library.md)  
**Next:** [Lesson 5.4: Deploying and Selecting Active Value Sets](lesson-5.4-deploying-and-selecting-active-value-sets.md)
