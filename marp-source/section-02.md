---
marp: true
theme: workshop
paginate: true
transition: fade
---


# Deployment Pipelines

Moving Fabric content from Dev → Prod

---

# Why Separate Environments?

<div class="comparison">

<div>
<h4>❌ Without Environments</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-red">Developers break production</div>
  <div class="box box-sm bg-red">Users see half-finished work</div>
  <div class="box box-sm bg-red">No way to test before go-live</div>
  <div class="box box-sm bg-red">No audit trail of changes</div>
</div>
</div>

<div>
<h4>✅ With Environments</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-green">Dev is isolated from production</div>
  <div class="box box-sm bg-green">Test before promoting</div>
  <div class="box box-sm bg-green">Controlled, deliberate releases</div>
  <div class="box box-sm bg-green">Clear history of what deployed</div>
</div>
</div>

</div>

---

# Fabric Deployment Pipelines

A Fabric feature that lets you **deploy content between workspaces** in stages

<div class="flow" style="margin: 30px 0;">
  <div class="card card-dev">
    <div class="card-title">🛠️ Development</div>
    <div class="card-subtitle-sm">Build & iterate</div>
  </div>
  <span class="arrow-lg">→</span>
  <div class="card card-prod">
    <div class="card-title">🏭 Production</div>
    <div class="card-subtitle-sm">Live for users</div>
  </div>
</div>

- Each stage is backed by a **separate Fabric workspace**
- Deploy **all items** or **selected items** between stages
- Pipelines can have **2 to 10 stages**

---

# How It Works

<div class="flow" style="margin: 20px 0;">
  <div class="card card-md card-dev">
    <div class="card-title-md">Dev Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-item bg-blue">Sales Bronze</div>
      <div class="box box-item bg-orange">Transform Orders</div>
      <div class="box box-item bg-purple">Sales Analysis</div>
      <div class="box box-item bg-yellow">Revenue Dashboard</div>
    </div>
  </div>
  <div class="flow-col-center">
    <div class="arrow-label-sm">Deploy</div>
    <span class="arrow-md">→</span>
  </div>
  <div class="card card-md card-prod">
    <div class="card-title-md">Prod Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-item bg-blue">Sales Bronze</div>
      <div class="box box-item bg-orange">Transform Orders</div>
      <div class="box box-item bg-purple">Sales Analysis</div>
      <div class="box box-item bg-yellow">Revenue Dashboard</div>
    </div>
  </div>
</div>

- Deployment **copies item definitions** from one workspace to another
- Items are **created or updated** in the target workspace
- Each workspace can have **different data connections** and **security settings**

---

# Tagging Releases

Use **Git tags** to mark a point-in-time snapshot of your codebase

<div class="timeline">
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot timeline-dot-tag"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot"></div>
  <div class="timeline-line"></div>
  <div class="timeline-dot timeline-dot-tag"></div>
</div>

<div class="timeline-labels">
  <div class="timeline-spacer"></div>
  <div class="timeline-spacer"></div>
  <div class="timeline-tag">🏷️ v1</div>
  <div class="timeline-spacer"></div>
  <div class="timeline-spacer"></div>
  <div class="timeline-spacer"></div>
  <div class="timeline-tag">🏷️ v2</div>
</div>

- Tags let you **label a release** (e.g., `v1`, `v2`)
- You can always **go back and view** what was in a release
- Tag before you deploy — it creates a **record of what went to production**

---

# The Release Workflow

<div class="centered-block">
<div class="left-aligned">

<div class="step">
  <div class="step-number">1</div>
  <div class="step-text">Build and test your changes in the <strong>Dev</strong> workspace</div>
</div>

<div class="step">
  <div class="step-number">2</div>
  <div class="step-text"><strong>Commit</strong> your changes to the Git repository</div>
</div>

<div class="step">
  <div class="step-number">3</div>
  <div class="step-text"><strong>Tag</strong> the release in Git (e.g., <code>v1</code>)</div>
</div>

<div class="step">
  <div class="step-number">4</div>
  <div class="step-text"><strong>Deploy</strong> from Dev → Prod using the deployment pipeline</div>
</div>

</div>
</div>

This gives you a **repeatable, auditable** release process
