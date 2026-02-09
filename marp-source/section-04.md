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
    <div class="card-title-sm">Dev Workspace</div>
    <div style="font-size: 0.5em; color: #555;">main (merged code)</div>
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
- Done? Delete the branch — or **keep your workspace** and switch it to the next feature branch

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
