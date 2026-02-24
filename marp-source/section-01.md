---
marp: true
theme: workshop
paginate: true
transition: fade
---

# Git Basics for Fabric

Source control, commits, and your safety net

---

# Why Source Control?

<div class="comparison">

<div>
<h4>❌ Without Source Control</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-red">Break something? Can't get it back</div>
  <div class="box box-sm bg-red">Which version is correct?</div>
  <div class="box box-sm bg-red">Who changed this, and why?</div>
  <div class="box box-sm bg-red">No audit trail</div>
</div>
</div>

<div>
<h4>✅ With Source Control</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-green">Mistakes are reversible</div>
  <div class="box box-sm bg-green">One file, complete history</div>
  <div class="box box-sm bg-green">Every change attributed & timestamped</div>
  <div class="box box-sm bg-green">Full audit trail with commit messages</div>
</div>
</div>

</div>

**Source control isn't just for software developers** — it's for anyone who creates things that change over time and matter to the business.

---

# The Problem We've All Had

<div class="centered-block">
<div style="background: #f5f5f5; border-radius: 10px; padding: 20px 30px; font-family: monospace; font-size: 0.7em; line-height: 1.8;">
  📄 sales_report.pbix<br/>
  📄 sales_report_v2.pbix<br/>
  📄 sales_report_FINAL.pbix<br/>
  📄 sales_report_FINAL_v2.pbix<br/>
  📄 sales_report_FINAL_v2_fixed.pbix<br/>
  📄 sales_report_FINAL_v2_fixed_USE_THIS_ONE.pbix
</div>
</div>

**Git solves this:** One file, complete history. Every version is preserved with a clear message explaining what changed and why.

---

# What is a Commit?

A **snapshot** of your work at a specific point in time

<div class="flow" style="margin: 30px 0; gap: 4px;">
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
</div>

Each commit records:
- **What** changed (the diff)
- **Who** made the change (the author)
- **When** it happened (the timestamp)
- **Why** it was made (the commit message)

Think of it like a save point in a video game — you can always come back to it.

---

# How Fabric + Git Works

<div class="flow" style="margin: 16px 0;">
  <div class="card card-sm card-workspace">
    <div class="card-title-sm">🏢 Fabric Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-xs bg-blue">Sales Bronze</div>
      <div class="box box-xs bg-orange">Transform Orders</div>
      <div class="box box-xs bg-purple">Sales Analysis</div>
      <div class="box box-xs bg-yellow">Revenue Dashboard</div>
    </div>
  </div>
  <div class="flow-col-center">
    <div class="arrow-label">Commit/Push →</div>
    <span class="arrow-md">⇄</span>
    <div class="arrow-label">← Pull</div>
  </div>
  <div class="card card-sm card-git">
    <div class="card-title-sm">🔀 Git Repository</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-xs bg-mono">Sales Bronze.Lakehouse/</div>
      <div class="box box-xs bg-mono">Transform Orders.Notebook/</div>
      <div class="box box-xs bg-mono">Sales Analysis.SemanticModel/</div>
      <div class="box box-xs bg-mono">Revenue Dashboard.Report/</div>
    </div>
  </div>
</div>

- **Commit/Push** — save and push changes from your workspace to Git
- **Pull** — pull changes from Git into your workspace
- Fabric **serializes** each item as files/folders in the repo

---

# Change Tracking in Fabric

When something changes, Fabric tells you:

<div class="centered-block">
<div class="left-aligned" style="gap: 16px;">

<div class="step">
  <div style="border-radius: 6px; padding: 6px 12px; background: #28A745; color: #fff; font-size: 0.8em; font-weight: bold; min-width: 24px; text-align: center;">+</div>
  <div class="step-text"><strong>New item</strong> — exists in workspace but not yet in Git</div>
</div>

<div class="step">
  <div style="border-radius: 6px; padding: 6px 12px; background: #D4A843; color: #fff; font-size: 0.8em; font-weight: bold; min-width: 24px; text-align: center;">≠</div>
  <div class="step-text"><strong>Modified</strong> — item changed since last commit</div>
</div>

<div class="step">
  <div style="border-radius: 6px; padding: 6px 12px; background: #DC3545; color: #fff; font-size: 0.8em; font-weight: bold; min-width: 24px; text-align: center;">−</div>
  <div class="step-text"><strong>Deleted</strong> — item removed from workspace but still in Git</div>
</div>

</div>
</div>

These indicators appear in the workspace item list and the Source control panel.

---

# Writing Good Commit Messages

<div class="comparison" style="gap: 60px;">

<div>
<h4>❌ Bad</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-red">"fix"</div>
  <div class="box box-sm bg-red">"updates"</div>
  <div class="box box-sm bg-red">"changed stuff"</div>
  <div class="box box-sm bg-red">"WIP"</div>
</div>
</div>

<div>
<h4>✅ Good</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-green" style="font-weight: normal; text-align: left;">Fix null pointer in data transformation</div>
  <div class="box box-sm bg-green" style="font-weight: normal; text-align: left;">Add customer segmentation logic</div>
  <div class="box box-sm bg-green" style="font-weight: normal; text-align: left;">Update connection string for prod</div>
</div>
</div>

</div>

<br/>

**Tips:** Be specific, use present tense, keep the first line short (~50 chars)

---

# Undoing Mistakes

Your safety net: **Undo** discards uncommitted changes and restores from Git

<div class="flow" style="margin: 20px 0;">
  <div class="card card-dev" style="padding: 12px 16px;">
    <div class="card-title-md">✅ Last Commit</div>
    <div class="card-subtitle-sm">Working notebook</div>
  </div>
  <span class="arrow-lg">→</span>
  <div class="card" style="border: 2px solid #DC3545; background: #fde8e8; padding: 12px 16px;">
    <div class="card-title-md">💥 Your Change</div>
    <div class="card-subtitle-sm">Added broken code</div>
  </div>
  <span class="arrow-lg">→</span>
  <div class="card card-dev" style="padding: 12px 16px;">
    <div class="card-title-md">✅ After Undo</div>
    <div class="card-subtitle-sm">Back to working</div>
  </div>
</div>

| Scenario | Use Undo? |
|----------|-----------|
| Uncommitted changes you don't want | ✅ Yes |
| Want to start fresh from last commit | ✅ Yes |
| Already committed the changes | ❌ No — use Pull Requests (Section 4) |

---

# What You'll Do in Section 1

<div class="centered-block">
<div class="left-aligned">

<div class="step">
  <div class="step-number">1</div>
  <div class="step-text">Create a Fabric workspace and connect it to <strong>Git</strong></div>
</div>

<div class="step">
  <div class="step-number">2</div>
  <div class="step-text">Create a notebook and make your <strong>first commit</strong></div>
</div>

<div class="step">
  <div class="step-number">3</div>
  <div class="step-text">Make changes, commit again, and view <strong>history</strong></div>
</div>

<div class="step">
  <div class="step-number">4</div>
  <div class="step-text">Practice <strong>undoing</strong> uncommitted changes</div>
</div>

</div>
</div>

Let's get started!
