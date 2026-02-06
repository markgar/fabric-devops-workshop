# Lesson 5.1: What Are Variable Libraries?

## Why This Lesson?

So far, we’ve handled environment differences (Dev/Prod) using things like deployment rules and careful workspace setup. But as your solution grows, you’ll start to accumulate settings that vary by environment:

- Table names
- Row counts for sample data
- Feature flags
- Workspace or lakehouse references

Hard-coding those values inside notebooks or pipelines creates two problems:

1. You have to edit code to change configuration.
2. It becomes easy for Dev settings to accidentally leak into Prod.

**Variable libraries solve this** by giving us a single place to define variables (settings) and then choose different values per environment.

---

## Overview

In this lesson, you will:

- Learn what a variable library is in Microsoft Fabric
- Understand variables, value sets, and the “active value set per stage” idea
- Decide what we’ll configure in our workshop example

**Estimated Time:** 5-10 minutes

**Prerequisites:**
- Completed Section 4 (Feature Branches)
- A deployment pipeline with Dev → Prod workspaces

---

## Understand the Core Concepts

A variable library is a Fabric item that contains:

- **Variables** (like `RowCount` or `TableName`)
- **Value sets** (like `Dev` and `Prod`) that provide different values for the same variables

The key behavior to understand:

- All value sets exist in the library.
- Each stage in your deployment pipeline chooses one value set to be **active**.
- Your notebooks/pipelines read variables from the active value set for the stage they’re running in.

> 💡 Think of a value set like an “environment profile” for the same variable list.

---

## Our Workshop Example

We’ll use a simple notebook that generates its own data (no external data sources) and writes it to the default lakehouse.

We’ll drive these settings from a variable library:

- `RunLabel` — a string like `dev` or `prod` that we print and write into the data
- `RowCount` — how many rows to generate per run
- `TableName` — which lakehouse table to write to

> 💡 Optional: If you later add a **Test** stage (as discussed in Section 2), you can add a `Test` value set too. This workshop sticks to Dev → Prod.

> ✅ This makes it easy to prove the configuration changed per stage.

---

## Summary

In this lesson, you:

- ✅ Learned what variable libraries are and why they matter
- ✅ Understood variables vs value sets
- ✅ Picked a small set of settings to manage via a library

---

**Previous:** [Lesson 4.6: Cleaning Up](../section-04-feature-branches/lesson-4.6-cleaning-up.md)  
**Next:** [Lesson 5.2: Creating a Variable Library](lesson-5.2-creating-a-variable-library.md)
