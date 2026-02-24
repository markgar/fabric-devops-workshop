---
marp: true
theme: workshop
paginate: true
transition: fade
---


# Feature Branches

Isolated development, safe merging, and working as a team

---

# The Problem with Sharing

So far, everyone works in **one Dev workspace** and commits straight to `main`

<div class="flow" style="margin: 20px 0;">
  <div class="card card-md card-dev">
    <div class="card-title-md">Dev Workspace</div>
    <div class="flow-col" style="margin-top: 8px; gap: 4px;">
      <div class="box box-xs bg-blue-muted">Alice editing notebook</div>
      <div class="box box-xs bg-blue-muted">Bob editing report</div>
      <div class="box box-xs bg-blue-muted">Carol fixing model</div>
    </div>
  </div>
  <div class="flow-col-center">
    <div class="arrow-label-sm">Commit</div>
    <span class="arrow-md">→</span>
  </div>
  <div class="card card-md card-git">
    <div class="card-title-md">main branch</div>
    <div class="flow-col" style="margin-top: 8px; gap: 4px;">
      <div class="box box-xs bg-red">Half-finished features</div>
      <div class="box box-xs bg-red">Overwritten changes</div>
      <div class="box box-xs bg-red">Broken deployments</div>
    </div>
  </div>
</div>

**In traditional dev**, everyone has their own machine. In Fabric, workspaces are shared — so we need another way to isolate work.

---

# Inner Loop vs Outer Loop

Two development cycles that shape how you work:

<div class="comparison" style="gap: 40px;">

<div>
<h4>🔁 Inner Loop</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-blue-muted">Code → Test → Fix → Repeat</div>
  <div class="box box-sm bg-blue-muted">Your personal dev workspace</div>
  <div class="box box-sm bg-blue-muted">Fast — seconds to minutes</div>
  <div class="box box-sm bg-blue-muted">Private — just you</div>
</div>
</div>

<div>
<h4>🚀 Outer Loop</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-green">Commit → Review → Deploy</div>
  <div class="box box-sm bg-green">Git repo + deployment pipeline</div>
  <div class="box box-sm bg-green">Slower — minutes to hours</div>
  <div class="box box-sm bg-green">Shared — team and users</div>
</div>
</div>

</div>

**The challenge:** In Fabric, workspaces are shared — so each developer needs their **own workspace** and **own branch** to get a private inner loop.

---

# Feature Branches + Workspaces

Each developer gets their **own branch** and their **own workspace**

<div class="flow" style="margin: 16px 0; gap: 20px;">
  <div class="flow-col" style="gap: 8px;">
    <div class="card card-sm" style="border: 2px solid #6C8EBF; background: #e8eef7; padding: 10px 14px;">
      <div class="card-title-sm">Alice-Dev</div>
      <div style="font-size: 0.5em; color: #555;">feature-sales-report</div>
    </div>
    <div class="card card-sm" style="border: 2px solid #6C8EBF; background: #e8eef7; padding: 10px 14px;">
      <div class="card-title-sm">Bob-Dev</div>
      <div style="font-size: 0.5em; color: #555;">feature-fix-model</div>
    </div>
  </div>
  <div class="flow-col-center">
    <div style="font-size: 0.55em; color: #555; font-weight: bold;">Pull Request</div>
    <span class="arrow-md">→</span>
  </div>
  <div class="card card-sm card-dev" style="padding: 10px 14px;">
    <div class="card-title-sm">🔒 CI Workspace</div>
    <div style="font-size: 0.5em; color: #555;">main (merged code)</div>
    <div style="font-size: 0.45em; color: #2E8B57; font-weight: bold;">Read only — no direct commits</div>
  </div>
  <div class="flow-col-center">
    <div class="arrow-label-sm">Deploy</div>
    <span class="arrow-md">→</span>
  </div>
  <div class="card card-sm card-prod" style="padding: 10px 14px;">
    <div class="card-title-sm">Prod</div>
    <div style="font-size: 0.5em; color: #555;">main (via pipeline)</div>
  </div>
</div>

- **Branch policies** block direct commits to `main`
- **Pull requests** are the only way in — with review and approval
- **Branch out** in Fabric creates the branch + workspace in one step
- Done? Delete the branch in **GitHub** — or **keep your workspace** and switch it to the next feature branch

---

# What You'll Do in Section 4

<div class="centered-block">
<div class="left-aligned">

<div class="step">
  <div class="step-number">1</div>
  <div class="step-text">Learn about <strong>inner loop</strong> (your dev cycle) vs <strong>outer loop</strong> (team deployment)</div>
</div>

<div class="step">
  <div class="step-number">2</div>
  <div class="step-text">Configure <strong>branch policies</strong> to protect <code>main</code></div>
</div>

<div class="step">
  <div class="step-number">3</div>
  <div class="step-text">Create a <strong>feature branch</strong> and workspace with Branch out</div>
</div>

<div class="step">
  <div class="step-number">4</div>
  <div class="step-text">Merge your work with a <strong>pull request</strong> and clean up</div>
</div>

</div>
</div>

Let's get started!
