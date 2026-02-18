# Lesson 5.5: Other Ways to Use Variable Libraries

## Why This Lesson?

In Lesson 5.3, we used variable libraries from a notebook.

But notebooks aren’t the only place variable libraries can help.

This lesson is intentionally **discussion-only**: everything here is optional and you can complete the workshop without doing any of these integrations.

When your solution grows, you’ll usually want the *same* environment-specific values (workspace IDs, lakehouse IDs, connection IDs, flags, labels) to be reused across multiple Fabric items—without copy/pasting values everywhere.

---

## Overview

In this lesson, you will:

- See which Fabric items can consume a variable library
- Learn the common reference patterns you’ll see in each item type
- Get a quick “where to click” guide for each supported workload

**Estimated Time:** 10 minutes

**Prerequisites:**
- None (this is optional reading)

> ✅ You do not need to complete these steps to finish the workshop.

---

## Quick Map: Supported Items and Reference Styles

Microsoft Fabric variable libraries can be consumed by multiple item types.

| Item type | How you reference variables | Good for |
|---|---|---|
| Pipelines | Create a **Library variables** reference, then use expressions like `@pipeline().libraryVariables.<ReferenceName>` | Parameterizing activity settings (connections, table names, flags, etc.) |
| Lakehouse shortcuts (Preview) | Assign a variable to a shortcut property via **Manage shortcut** > **Edit variables** | Keeping shortcuts pointing at the right environment |
| Dataflow Gen2 with CI/CD (Preview) | Use Power Query functions `Variable.Value(...)` / `Variable.ValueOrDefault(...)` with a `$(/**/Library/Variable)` identifier | Making M queries environment-aware |
| Copy job | Link Copy job connections to a variable library | Connection parameterization across environments |
| User data functions | Connect to a variable library and read values via `FabricVariablesClient.getVariables()` | Centralized config for code-based functions |

> 💡 Most “direct reference” integrations use the identifier format: `$(/**/LibraryName/VariableName)`.

---

## Use Variable Library Variables in a Pipeline

Pipelines are often the first place you’ll want variable libraries beyond notebooks.

> 💡 Optional: You can skip this section and still complete the workshop.

1. In your workspace, create a new **Pipeline** (or open an existing one)
2. In the bottom panel, open the **Library variables** tab
3. Select **+ New**
4. Create a reference to a variable in your `EnvConfig` library (example):
   - **Name**: `RunLabel`
   - **Library**: `EnvConfig`
   - **Variable name**: `RunLabel`
   - **Type**: `String`
5. In an activity setting that supports dynamic content, select **Add dynamic content**
6. If needed, open the expression builder’s **Library variables** picker and select `RunLabel`

You should see an expression similar to:

`@pipeline().libraryVariables.RunLabel`

7. Save and run the pipeline

> ✅ The pipeline resolves the value based on the variable library’s active value set in that workspace (Dev vs Prod).

---

## Use Variables in Lakehouse Shortcuts (Preview)

You can assign variable library values to shortcut properties so shortcuts stay “environment-correct” after deployment.

> 💡 Optional: This is a nice-to-have pattern for real solutions, not required for this workshop.

1. Open a lakehouse that contains a shortcut
2. Right-click the shortcut and select **Manage shortcut**
3. Select **Edit variables**
4. Choose the shortcut property you want to parameterize (for example, a connection-related field)
5. Pick a variable from your variable library

> ⚠️ Shortcut variable assignment is a preview feature.

> ⚠️ Only variables of type `String` are supported for shortcut assignment.

---

## Use Variables in Dataflow Gen2 with CI/CD (Preview)

Dataflow Gen2 (with CI/CD) can reference variable libraries from Power Query (M).

> 💡 Optional: This workshop doesn’t require you to build a Dataflow Gen2.

1. Open your **Dataflow Gen2 with CI/CD**
2. In the query script, reference variable library values using one of these functions:
   - `Variable.ValueOrDefault(identifier, defaultValue)`
   - `Variable.Value(identifier)`
3. Use the identifier format `$(/**/LibraryName/VariableName)`

Example:

```M
Variable.ValueOrDefault("$(/**/EnvConfig/RunLabel)", "dev")
```

> ⚠️ The Power Query editor doesn’t currently evaluate variables during authoring. Use `Variable.ValueOrDefault(...)` so your query can still be edited and tested.

---

## Use Variables to Parameterize Copy Job Connections

Copy job supports using variable libraries to parameterize connection values.

> 💡 Optional: This workshop doesn’t require creating a Copy job.

1. Create variables in a variable library that represent your connection IDs
2. Create alternate value sets (for example, `Prod`) with the Prod connection IDs
3. Open your Copy job
4. In the source and destination connection configuration, link them to the variable library

> 💡 This pattern lets you deploy the same Copy job across environments while injecting the right connection per stage.

---

## Use Variables from User Data Functions

If you’re building Fabric User data functions, you can read variable library values as configuration.

> 💡 Optional: This workshop doesn’t require creating user data functions.

1. In your **User data functions** item, open **Manage connections**
2. Add a connection to your variable library and note the generated alias
3. In code, connect the variable library to your function and read variables using the `FabricVariablesClient`

Example pattern:

- Add a connection decorator for the variable library
- Call `getVariables()`
- Read the values via `.get("NAME")` or `["NAME"]`

> ✅ This is a good fit when you want config-driven behavior without redeploying code.

---

## Summary

In this lesson, you:

- ✅ Learned the supported items that can consume variable libraries
- ✅ Saw the reference patterns used by pipelines, Dataflows, shortcuts, Copy jobs, and user data functions
- ✅ Identified where variable libraries remove hard-coded environment values

> ✅ Reminder: everything in this lesson is optional and meant for awareness.

---

## References

- Variable libraries (supported items): https://learn.microsoft.com/en-us/fabric/cicd/variable-library/variable-library-overview#supported-items
- Pipelines: https://learn.microsoft.com/en-us/fabric/data-factory/variable-library-integration-with-data-pipelines
- Lakehouse shortcuts (Preview): https://learn.microsoft.com/en-us/fabric/onelake/assign-variables-to-shortcuts
- Dataflow Gen2 (Preview): https://learn.microsoft.com/en-us/fabric/data-factory/dataflow-gen2-variable-library-integration
- Copy job: https://learn.microsoft.com/en-us/fabric/data-factory/cicd-copy-job
- User data functions: https://learn.microsoft.com/en-us/fabric/data-engineering/user-data-functions/connect-to-data-sources#get-variables-from-fabric-variable-libraries

---

**Previous:** [Lesson 5.4: Deploying and Selecting Active Value Sets](lesson-5.4-deploying-and-selecting-active-value-sets.md)  
**Next:** [Workshop Outline](../../README.md)
